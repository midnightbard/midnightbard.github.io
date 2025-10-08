--- 
title: Shop
layout: simplepage
image: 
description:  
category: diary

---
<style>

    
    .custom-btn {
    color: #ffffff !important; /* White text color */
    text-decoration: none; /* Remove underline */
}

.custom-btn:hover,
.custom-btn:focus,
.custom-btn:active {
    color: #ffffff !important; /* Ensure white text on hover, focus, and active states */
}

</style>

<div class="container py-12">


<span class="ipa">
<div class="row g-4">
<!-- LIVE STREAM TIPS -->
<div class="col-12 col-md-6 col-lg-4">
<article class="card h-100 shadow-sm">
<img src="https://i.imgur.com/XmbEGku.png" class="card-img-top" alt="Post 1 thumbnail" />
<div class="card-body">
<div class="d-flex gap-2 mb-2">
<span class="badge text-bg-primary">Tips</span>

</div>
<h5 class="card-title mb-2">Personal tarot reading</h5>
<p class="card-text text-muted">
    Tip and receive your personal reading via email or on YouTube Community tab within 24H.
</p>
    
</div>
<div class="card-footer border-1 pt-0">
<div class="d-flex align-items-center justify-content-between">



    <style>

    
    .custom-btn {
    color: #ffffff !important; /* White text color */
    text-decoration: none; /* Remove underline */
}

.custom-btn:hover,
.custom-btn:focus,
.custom-btn:active {
    color: #ffffff !important; /* Ensure white text on hover, focus, and active states */
}

</style>




<script>
  fetch('http://ip-api.com/json/')
    .then(response => response.json())
    .then(data => {
      const blockedCountries = [
        'CN', 'IN', 'BD', 'PK', 'LK', 'NP', 'MV', 'BT', 'AF', 'AL', 'DZ', 'AZ', 'BH', 'BA', 'BN', 'BF', 
        'TD', 'KM', 'DJ', 'EG', 'GA', 'GM', 'GN', 'GW', 'ID', 'IR', 'IQ', 'JO', 'XK', 'KW', 'KG', 'LB', 
        'LY', 'MY', 'ML', 'MR', 'MA', 'NE', 'NG', 'OM', 'PS', 'QA', 'SA', 'SN', 'SL', 'SO', 'SD', 'SY', 
        'TJ', 'TN', 'TR', 'TM', 'AE', 'UZ', 'YE', 'AR', 'BO', 'BR', 'CL', 'CO', 'EC', 'GY', 'PY', 'PE', 
        'SR', 'UY', 'VE', 'AO', 'BJ', 'BW', 'BI', 'CM', 'CV', 'CF', 'CG', 'CD', 'CI', 'GQ', 'ER', 'ET', 
        'GH', 'KE', 'LS', 'LR', 'MG', 'MW', 'MU', 'MZ', 'NA', 'RW', 'ST', 'SC', 'ZA', 'SS', 'SZ', 'TZ', 
        'TG', 'UG', 'EH', 'ZM', 'ZW','HT', 'KI', 'SB', 'TL', 'TV', 'HR',
      ];
      const euCountries = ['AT', 'BE', 'BG', 'CY', 'CZ', 'DK', 'EE', 'FI', 'FR', 'DE', 'GR', 'HU', 'IE', 'IT', 'LV', 'LT', 'LU', 'MT', 'NL', 'PL', 'PT', 'RO', 'SK', 'SI', 'ES', 'SE', 'MC']; // EU

      const tipButton = document.getElementById('tipButton');
      const affiliateTipButton = document.getElementById('affiliateTipButton');
      const euTipButton = document.getElementById('euTipButton');

      if (blockedCountries.includes(data.countryCode)) {
        // Show affiliate button for blocked countries
        if (tipButton) tipButton.style.display = 'none';
        if (euTipButton) euTipButton.style.display = 'none';
        if (affiliateTipButton) affiliateTipButton.style.display = 'inline-block';
      } else if (euCountries.includes(data.countryCode)) {
        // Show EU button for Croatia
        if (tipButton) tipButton.style.display = 'none';
        if (affiliateTipButton) affiliateTipButton.style.display = 'none';
        if (euTipButton) euTipButton.style.display = 'inline-block';
      } else {
        // Show regular tip button for other countries
        if (affiliateTipButton) affiliateTipButton.style.display = 'none';
        if (euTipButton) euTipButton.style.display = 'none';
        if (tipButton) tipButton.style.display = 'inline-block';
      }
    })
    .catch(error => console.error('Error fetching GeoIP:', error));
</script>

<div style="padding-bottom: 10px;" class="d-flex justify-content-left align-items-center gap-2">

    
<a class="btn btn-primary custom-btn" href="https://ko-fi.com/c/428197384e" role="button">KoFi</a>

    <button id="affiliateTipButton" type="button" class="btn btn-danger" data-bs-toggle="modal" data-bs-target="#affiliatePricingModal" style="display: none;">
        <i class="bi bi-globe"></i> Discount 
    </button>


    
    
</div>

<!-- Pay Modal for extra Countries -->
<div class="modal fade" id="affiliatePricingModal" tabindex="-1" aria-labelledby="affiliatePricingModalLabel" aria-hidden="true">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="affiliatePricingModalLabel"><i class="bi bi-globe"></i>  Tips - Africa - Asia - India <img src="https://flagcdn.com/24x18/in.png" alt="India">  <img src="https://flagpedia.net/data/org/w1160/au.webp" style="width:24px;height:18px;" alt="Africa Union"> </h5>
                <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body">
                
                <form action="https://www.paypal.com/cgi-bin/webscr" method="post" target="_top">
  <input type="hidden" name="cmd" value="_s-xclick" />
  <input type="hidden" name="hosted_button_id" value="FWH5ENQYZB5XS" />
  <table>
    <tr>
      <td>
        <input type="hidden" name="on0" value="Tips"/>
        Tips
      </td>
    </tr>
    <tr>
      <td>
        <select name="os0">
          <option value="Small reading">
            Small reading $1.00 USD
          </option>
          <option value="2 questions + Energy">
            2 questions + Energy $2.00 USD
          </option>
          <option value="General, multiple">
            General, multiple $5.00 USD
          </option>
        </select>
      </td>
    </tr>
    <tr>
      <td>
        <input type="hidden" name="on1" value="Message - questions"/>
        Message - questions
      </td>
    </tr>
    <tr>
      <td>
        <input type="text" name="os1" maxLength="200" />
      </td>
    </tr>
    <tr>
      <td>
        <input type="hidden" name="on2" value="Where to send - email, YouTube ????"/>
        Where to send - email, YouTube ????
      </td>
    </tr>
    <tr>
      <td>
        <input type="text" name="os2" maxLength="200" />
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

    
    
<!--
<button type="button" class="btn btn-info text-white" data-bs-toggle="modal" data-bs-target="#infoModal">
        Instructions
    </button>

<div class="modal fade" id="infoModal" tabindex="-1" aria-labelledby="infoModalLabel" aria-hidden="true">
    <div class="modal-dialog modal-lg">
        <div class="modal-content pricing-content-moonlight">
            <div class="modal-header pricing-header-moonlight">
                <h5 class="modal-title" id="infoModalLabel"><i class="bi bi-info-circle"></i> In case there are no new readings...</h5>
                <button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body pricing-body-moonlight">
                <p>When I am not live, you can still order your reading the same way you would on a livestream. Please send me a clear question. If your reading involves more than one question or needs more detail, use the chat to describe what you want.</p>
                <p>I will definitely receive all your messages. Since the chat doesn't require a login, please leave an email or social media account so I can reach you in case that you need additional info.
                </p>
                <p>
                You can also read more about payments and discounts which I included for specific countries. 
                </p>
                <p>During broadcasts/prerecorded live streams follow instructions - your reading will be delivered either to an email associated with your Paypal account, an email that you specify or if you use YouTube in comments under that braodcast or live stream. You will receive notification once your YouTube reading is done.  </p>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
                <a class="btn btn-primary custom-btn" href="/shop/live-stream-tips/">
                    Details
                </a>
            </div>
        </div>
    </div>
</div> -->

    
</div>
</div>
</article>
</div>


<!-- NATAL CHART -->
<div class="col-12 col-md-6 col-lg-4">
<article class="card h-100 shadow-sm">
<img src="https://i.imgur.com/hT0gdBJ.png" class="card-img-top" alt="Post 2 thumbnail" />
<div class="card-body">
<div class="d-flex gap-2 mb-2">
<span class="badge text-bg-dark">Astrology</span>
</div>
<h5 class="card-title mb-2">Natal Chart </h5>
<p class="card-text text-muted">
Full natal chart analyses/comparative analyses for two people. Full time, date and place of birth ( comparative for both). 
</p>

</div>
<div class="card-footer border-0 pt-0">
<div class="d-flex align-items-center justify-content-between">
    <a class="btn btn-primary custom-btn" href="/shop/sidereal-natal" role="button">PayPal</a>

    
 
    
</div>
</div>
</article>
</div>


<!-- CELEBRITY VIDEOS -->
<div class="col-12 col-md-6 col-lg-4">
<article class="card h-100 shadow-sm">
<img src="https://i.imgur.com/GBLRM49.png" class="card-img-top" alt="Post 3 thumbnail" />
<div class="card-body">
<div class="d-flex gap-2 mb-2">
<span class="badge text-bg-info">Celebrity</span>
</div>
<h5 class="card-title mb-2">Celebrity Tarot</h5>
<p class="card-text text-muted">
Tarot and oracle reading about your favorite celebrity, public person or a company. 
</p>
    
    
    
</div>
<div class="card-footer border-0 pt-0">
<div class="d-flex align-items-center justify-content-between">
    <a class="btn btn-danger custom-btn" href="" role="button">Pending...</a>

    
    
    
</div>
</div>
</article>
</div>
</div>
    </span>
