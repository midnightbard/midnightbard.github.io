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
    
    .modal {
      max-width: 100%;
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
  <div class="modal-dialog modal-lg">
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
<div class="modal fade" id="pricingModalMoonlight" tabindex="-1" aria-labelledby="pricingModalLabelMoonlight" aria-hidden="true">
  <div class="modal-dialog modal-lg">
    <div class="modal-content pricing-content-moonlight">
      <div class="modal-header pricing-header-moonlight">
        <h5 class="modal-title" id="pricingModalLabelMoonlight"><i class="bi bi-globe"></i> <i class="bi bi-currency-dollar"></i> Tips - International <img src="https://flagcdn.com/24x18/us.png" alt="United States">   </h5>
        <button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body pricing-body-moonlight">
          <p>Use private chat to ask. Your live reading starts after tip, and your messages stay private.The higher the tip, the deeper and more detailed your reading will be. </p>
          <form action="https://www.paypal.com/cgi-bin/webscr" method="post" target="_top">
  <input type="hidden" name="cmd" value="_s-xclick" />
  <input type="hidden" name="hosted_button_id" value="94EFKHDSXWJ26" />
  <table>
    <tr>
      <td>
        <input type="hidden" name="on0" value="What are you buying?"/>
        What are you buying?
      </td>
    </tr>
    <tr>
      <td>
        <select name="os0">
          <option value="One Question ">
            One Question  $5.00 USD
          </option>
          <option value="Two question + energy reading">
            Two question + energy reading $10.00 USD
          </option>
          <option value="General - multiple ">
            General - multiple  $20.00 USD
          </option>
        </select>
      </td>
    </tr>
  </table>
  <input type="hidden" name="currency_code" value="USD" />
  <input type="image" src="https://www.paypalobjects.com/en_US/i/btn/btn_buynowCC_LG.gif" border="0" name="submit" title="PayPal - The safer, easier way to pay online!" alt="Buy Now" />
</form>
          
          
          
        
      </div>
         <div class="modal-footer">
                <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
               <a class="btn btn-primary custom-btn" href="/shop/live-stream-tips/">
                    Details
                </a>
            </div>
    </div>
  </div>
</div>

    
    <hr/>
<h3>Incoming live streams</h3> 

<div id="upcoming-container"></div>
    
    <hr/>
<sup><i style="color:red!important;" class="bi bi-bell-fill"></i> <b>Click on frame to see time of a live stream, click on title to go on YouTube and subscribe to notification.</b></sup>
</div>

<script>
    const videos = [

        { id: 'sQLCqd5U5WM' }
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