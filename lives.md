---
title: Lives
layout: live-template
image: 
description:  
comments: true
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

    /* Main player default (desktop horizontal) */
    #main-player-container {
        position: relative;
        padding-bottom: 56.25%; /* 16:9 horizontal */
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
        grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
        gap: 20px;
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
    .upcoming-title {
        text-align: center;
        padding: 10px 0;
        font-size: 1em;
        font-weight: bold;
    }
    a:hover { 
        color: black!important; 
    }

    /* Mobile: make main player vertical (portrait) */
    @media (max-width: 768px) {
        #main-player-container {
            padding-bottom: 177.78%; /* 9:16 vertical */
        }
    }
</style>

<div class="container">
    <div id="main-player-container"></div>
    
    <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#quickLinksModal">
  <i class="bi bi-list" style="font-size: 1.5rem;"></i>
</button>
    <button type="button" class="btn btn-secondary" data-bs-toggle="modal" data-bs-target="#pricingModalMoonlight">
  View Pricing
</button>
    
        <script src="https://gumroad.com/js/gumroad.js"></script>
    <a style="color:black!important; text-decoration:none;" class="gumroad-button" href="https://midnightbard.gumroad.com/l/youtube-tarot" data-gumroad-overlay-checkout="true">Tip</a>
        
    <div id="main-video-title"></div>
    


<!-- Modal -->
<div class="modal fade" id="quickLinksModal" tabindex="-1" aria-labelledby="quickLinksLabel" aria-hidden="true">
  <div class="modal-dialog modal-sm">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="quickLinksLabel">Quick Links</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        <a href="/" class="d-block mb-2"><i class="bi bi-cloud-moon"></i> Home</a>
        <a href="/shop" class="d-block mb-2"><i class="bi bi-bag"></i> Shop</a>
        <a href="/activity" class="d-block"><i class="bi bi-book"></i> Activity</a>
      </div>
    </div>
  </div>
</div>
    
    


<!-- Modal -->
<div class="modal fade pricing-modal-moonlight" id="pricingModalMoonlight" tabindex="-1" aria-labelledby="pricingModalLabelMoonlight" aria-hidden="true">
  <div class="modal-dialog modal-sm">
    <div class="modal-content pricing-content-moonlight">
      <div class="modal-header pricing-header-moonlight">
        <h5 class="modal-title" id="pricingModalLabelMoonlight">Service Pricing</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body pricing-body-moonlight">
        <p class="pricing-text-moonlight">
          Click on <b>Configure</b> during checkout to choose from options below<br/>
          <small>$5 – one question</small><br/>
          <small>$10 – two questions</small><br/>
          <small>$20 – general reading</small><br/>
        </p>
      </div>
    </div>
  </div>
</div>


    
    <h2>Incoming live streams</h2> 
    <hr/>
    <b>Click to see exact date and time. </b>
    <div id="upcoming-container"></div>
</div>

<script>
    const API_KEY = "AIzaSyCNfUp8j1ZawWbnW2Urdd2CiNmOgDxfW7M"; // Replace with your restricted YouTube API key
    const CHANNEL_ID = "UC56rhF2RMN78IpN9KIFSQUg"; // Replace with your channel ID

    // Fetch upcoming livestreams from your channel
    async function fetchUpcomingStreams() {
        const url = `https://www.googleapis.com/youtube/v3/search?key=${API_KEY}&channelId=${CHANNEL_ID}&part=snippet&eventType=upcoming&type=video&order=date&maxResults=10`;
        const response = await fetch(url);
        const data = await response.json();
        return data.items.map(item => ({
            id: item.id.videoId,
            title: item.snippet.title
        }));
    }

    // Load main player
    function loadMainPlayer(videoId, title) {
        const playerContainer = document.getElementById('main-player-container');
        const titleContainer = document.getElementById('main-video-title');

        playerContainer.innerHTML = `
            <iframe src="https://www.youtube.com/embed/${videoId}?autoplay=1&rel=0"
                    frameborder="0" 
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
                    allowfullscreen>
            </iframe>
        `;
        titleContainer.innerHTML = title ? title : '';
    }

    // Create upcoming livestream embed
    function createUpcomingEmbed(video) {
        const upcomingContainer = document.getElementById('upcoming-container');
        const videoDiv = document.createElement('div');
        videoDiv.className = 'upcoming-video';

        videoDiv.innerHTML = `
            <iframe src="https://www.youtube.com/embed/${video.id}?enablejsapi=1&rel=0&modestbranding=1" 
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
                allowfullscreen>
            </iframe>
            <div class="upcoming-title">${video.title}</div>
        `;

        // Clicking this embed loads it into the main player
        videoDiv.onclick = () => loadMainPlayer(video.id, video.title);

        upcomingContainer.appendChild(videoDiv);
    }

    // Initialize page
    async function initPage() {
        const videoLinks = await fetchUpcomingStreams();

        if (videoLinks.length === 0) {
            document.getElementById('main-player-container').innerHTML = `<p style="text-align:center; padding: 50px;">No upcoming videos.</p>`;
            return;
        }

        // Load first video with its title
        loadMainPlayer(videoLinks[0].id, videoLinks[0].title);

        // Create embedded upcoming live streams
        for (let i = 1; i < videoLinks.length; i++) {
            createUpcomingEmbed(videoLinks[i]);
        }
    }

    window.onload = initPage;
</script>
