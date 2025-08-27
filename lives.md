---
title: Lives
layout: live-template
---

<style>
    body {
        font-family: Arial, sans-serif;
        margin: 0;
        padding: 2px;
        background-color: #121212;
        color: #e0e0e0;
    }
    .container {
        max-width: 1200px;
        margin: auto;
    }
    h1 {
        text-align: center;
        color: #ffffff;
        margin-bottom: 20px;
    }

    #main-player-container {
        position: relative;
        padding-bottom: 56.25%;
        height: 0;
        overflow: hidden;
        background-color: #000;
        border-radius: 10px;
        box-shadow: 0 4px 15px rgba(0,0,0,0.5);
        margin-bottom: 15px;
    }

    #main-player-container iframe {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
    }

    #main-video-title {
        text-align: center;
        font-size: 1.3em;
        font-weight: bold;
        margin-bottom: 25px;
        color: #ffffff;
    }

    #upcoming-container {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(270px, 1fr));
    gap: 20px;
}

/* For screens up to 767px wide (typical mobile landscape and below) */
@media (max-width: 767px) {
    #upcoming-container {
        grid-template-columns: repeat(auto-fill, minmax(270px, 1fr));
        /* You can adjust the 200px value to whatever looks best on your site. */
    }
}

    .upcoming-video {
        background-color: #2c2c2c;
        border-radius: 8px;
        overflow: hidden;
        box-shadow: 0 2px 8px rgba(0,0,0,0.3);
        padding: 10px;
        cursor: pointer;
        transition: transform 0.2s ease-in-out;
    }
    .upcoming-video:hover {
        transform: translateY(-5px);
        box-shadow: 0 6px 15px rgba(0,0,0,0.5);
    }
    .upcoming-video iframe {
        width: 100%;
        height: 200px;
        border: none;
        border-radius: 6px;
    }

    a:hover { 
        color: black!important; 
    }

    @media (max-width: 768px) {
        #main-player-container {
            padding-bottom: 177.78%;
        }
    }
    
    .gisted {
      display: none;
    }
</style>

<div class="container">
    <div id="main-player-container"></div>
    <div id="main-video-title"></div>
    
    <script src="https://gumroad.com/js/gumroad.js"></script>
<!-- BUTTONS --->
    
{% include buttons.html %}
  
<!-- BUTTONS --->
    
<!-- Quick Links Modal -->
<div class="modal fade" id="quickLinksModal" tabindex="-1" aria-labelledby="quickLinksLabel" aria-hidden="true">
  <div class="modal-dialog modal-sm">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="quickLinksLabel">Quick Links</h5>
        <button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        <a href="/" class="d-block mb-2"><i class="bi bi-cloud-moon"></i> Home</a>
        <a href="/shop" class="d-block mb-2"><i class="bi bi-bag"></i> Shop</a>
        <a href="/activity" class="d-block"><i class="bi bi-book"></i> Activity</a>
      </div>
    </div>
  </div>
</div>

<!-- Pricing Modal -->
<div class="modal fade pricing-modal-moonlight" id="pricingModalMoonlight" tabindex="-1" aria-labelledby="pricingModalLabelMoonlight" aria-hidden="true">
  <div class="modal-dialog modal-sm">
    <div class="modal-content pricing-content-moonlight">
      <div class="modal-header pricing-header-moonlight">
        <h5 class="modal-title" id="pricingModalLabelMoonlight">INFO</h5>
        <button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body pricing-body-moonlight">
          <ul class="nav nav-tabs" id="tarotTabs" role="tablist">
    <li class="nav-item" role="presentation">
      <button class="nav-link active" id="info-tab" data-bs-toggle="tab" data-bs-target="#info" type="button" role="tab" aria-controls="info" aria-selected="true">Tarot Readings</button>
    </li>
    <li class="nav-item" role="presentation">
      <button class="nav-link" id="pricing-tab" data-bs-toggle="tab" data-bs-target="#pricing" type="button" role="tab" aria-controls="pricing" aria-selected="false">Pricing</button>
    </li>
  </ul>
          
          <div class="tab-content" id="tarotTabsContent">
    <div class="tab-pane fade show active" id="info" role="tabpanel" aria-labelledby="info-tab">
      <div class="p-3">
        Tarot readings are happening here; always ask before paying anything. You have access to a private chat to talk with the reader and a tip button to choose your desired option. Your live reading will begin once you've selected a service, and your chat messages will be invisible to others. 
      </div>
    </div>
    <div class="tab-pane fade" id="pricing" role="tabpanel" aria-labelledby="pricing-tab">
      <div class="p-3">
        Click on <b>Configure</b> during checkout to choose from options below<hr/>
        <small>$5 – one question</small><br>
        <small>$10 – two questions + oracle cards and free energy reading.</small><br>
        <small>$20 – general reading up to 30 minutes</small><hr/>
          Click Continue Shopping to come back on a page. <hr/>
          Your purchase privacy and security are fully protected by the Gumroad platform. 
      </div>
    </div>
  </div>
      </div>
    </div>
  </div>
</div>

<h2>Incoming live streams</h2> 
<hr/>
<b>Click to see time of a live stream and subscribe to notification. <i class="bi bi-bell-fill"></i></b>
<hr/>
<div id="upcoming-container"></div>
</div>

<script>
    const videos = [
        { id: 'BXJmB5fww28' },
        { id: 'X5M-u0HMHH4' },
        { id: 'GioQXrd2Cc8' }
    ];

    function loadMainPlayer(videoId) {
        document.getElementById('main-player-container').innerHTML = `
            <iframe src="https://www.youtube.com/embed/${videoId}?autoplay=1&rel=0"
                    frameborder="0" 
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
                    allowfullscreen>
            </iframe>`;
    }

    function createUpcomingEmbed(video) {
        const container = document.getElementById('upcoming-container');
        const div = document.createElement('div');
        div.className = 'upcoming-video';

        div.innerHTML = `
            <iframe src="https://www.youtube.com/embed/${video.id}?enablejsapi=1&rel=0&modestbranding=1" 
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
                allowfullscreen>
            </iframe>
        `;

        div.onclick = () => loadMainPlayer(video.id);
        container.appendChild(div);
    }

    function initPage() {
        if (videos.length === 0) {
            document.getElementById('main-player-container').innerHTML = `<p style="text-align:center; padding: 50px;">No upcoming videos.</p>`;
            return;
        }

        loadMainPlayer(videos[0].id);

        for (let i = 1; i < videos.length; i++) {
            createUpcomingEmbed(videos[i]);
        }
    }

    window.onload = initPage;
</script>

{% include crisp.html %}