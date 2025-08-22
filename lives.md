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

    a:hover { 
        color: black!important; 
    }

    @media (max-width: 768px) {
        #main-player-container {
            padding-bottom: 177.78%;
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

<!-- Quick Links Modal -->
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

<!-- Pricing Modal -->
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
<b>Click to see time of a live stream.</b>
<div id="upcoming-container"></div>
</div>

<script>
    const API_KEY = "AIzaSyCNfUp8j1ZawWbnW2Urdd2CiNmOgDxfW7M";
    const CHANNEL_ID = "UC56rhF2RMN78IpN9KIFSQUg";

    async function fetchUpcomingStreams() {
        // Get upcoming videos
        const searchUrl = `https://www.googleapis.com/youtube/v3/search?key=${API_KEY}&channelId=${CHANNEL_ID}&part=snippet&eventType=upcoming&type=video&order=date&maxResults=10`;
        const searchRes = await fetch(searchUrl);
        const searchData = await searchRes.json();

        if (!searchData.items) return [];

        // Extract video IDs
        const videoIds = searchData.items.map(item => item.id.videoId).join(',');

        // Get scheduledStartTime for correct ordering
        const detailsUrl = `https://www.googleapis.com/youtube/v3/videos?key=${API_KEY}&id=${videoIds}&part=liveStreamingDetails`;
        const detailsRes = await fetch(detailsUrl);
        const detailsData = await detailsRes.json();

        // Sort by scheduledStartTime (earliest first)
        const videos = detailsData.items
            .map(item => ({
                id: item.id,
                scheduledTime: item.liveStreamingDetails?.scheduledStartTime || ''
            }))
            .sort((a, b) => new Date(a.scheduledTime) - new Date(b.scheduledTime));

        return videos;
    }

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

    async function initPage() {
        const videos = await fetchUpcomingStreams();

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
