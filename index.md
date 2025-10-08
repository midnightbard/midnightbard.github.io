--- 
title: 
layout: home
image: 
description:  
category: diary
media: frontpage
---

<div class="profile-container">
  <div class="cover-image">
    <img src="/pictures/cover.jpeg" alt="Cover Image">
  </div>
  <div class="profile-image">
    <img src="/pictures/mb.png" alt="Profile Image">
    
  </div>
  
  
  
  <span style="float: right;">
    
    
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
        'TG', 'UG', 'EH', 'ZM', 'ZW','HT', 'KI', 'SB', 'TL', 'TV', 
      ];
      const euCountries = ['AT', 'BE', 'BG', 'CY', 'CZ', 'DK', 'EE', 'FI', 'FR', 'DE', 'GR', 'HU', 'IE', 'IT', 'LV', 'LT', 'LU', 'MT', 'NL', 'PL', 'PT', 'RO', 'SK', 'SI', 'ES', 'SE', 'HR', 'MC']; // EU

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




<div class="modal fade" id="affiliatePricingModal" tabindex="-1" aria-labelledby="affiliatePricingModalLabel" aria-hidden="true">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="affiliatePricingModalLabel"><i class="bi bi-globe"></i>  Tips - Africa - Asia - India <img src="https://flagcdn.com/24x18/in.png" alt="India">  <img src="https://flagpedia.net/data/org/w1160/au.webp" style="width:24px;height:18px;" alt="Africa Union"> </h5>
                <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body">
              
              
              You have discount based on location. <br/>
              Leave me either YouTube username or email. <br/>
                
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
   
      <button id="tipButton" type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#pricingModalMoonlight">
        <i class="bi bi-currency-dollar"></i> Tarot Reading
    </button>
    
    
    
    <!-- Pricing Modal -->
<div class="modal fade" id="pricingModalMoonlight" tabindex="-1" aria-labelledby="pricingModalLabelMoonlight" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content pricing-content-moonlight">
      <div class="modal-header pricing-header-moonlight">
        <h5 class="modal-title" id="pricingModalLabelMoonlight"><i class="bi bi-globe"></i> <i class="bi bi-currency-dollar"></i> Tips - International <img src="https://flagcdn.com/24x18/us.png" alt="United States">   </h5>
        <button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body pricing-body-moonlight">
          <p>Tip and receive your personal reading via email or on YouTube Community tab within 24H.  </p>
          
        <a href="https://ko-fi.com/c/428197384e">Commission</a> or 
          
          <iframe id='kofiframe' src='https://ko-fi.com/midnightbard/?hidefeed=true&widget=true&embed=true&preview=true' style='border:none;width:100%;padding:4px;background:#f9f9f9;' height='712' title='midnightbard'></iframe>
        
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
      
      
    
    <button id="euTipButton" type="button" class="btn btn-success" data-bs-toggle="modal" data-bs-target="#euPricingModal" style="display: none;">
        <i class="bi bi-currency-euro"></i> Tarot Reading
    </button>
    
    <!-- EU Modal  -->
<div class="modal fade" id="euPricingModal" tabindex="-1" aria-labelledby="euPricingModalLabel" aria-hidden="true">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="euPricingModalLabel"><i class="bi bi-currency-euro"></i>  Tips - <img src="https://flagcdn.com/24x18/eu.png" alt="European Union">  </h5>
                <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body">
                
                Based upon frivolous actions, you can get one free, or sponsor us: 
              <a href="https://ko-fi.com/midnightbard">Sponsor</a><iframe id='kofiframe' src='https://ko-fi.com/midnightbard/?hidefeed=true&widget=true&embed=true&preview=true' style='border:none;width:100%;padding:4px;background:#f9f9f9;' height='612' title='midnightbard'></iframe>
                <!--<form action="https://www.paypal.com/cgi-bin/webscr" method="post" target="_top">
  <input type="hidden" name="cmd" value="_s-xclick" />
  <input type="hidden" name="hosted_button_id" value="LBDUXS3VUCVZJ" />
  <table>
    <tr>
      <td>
        <input type="hidden" name="on0" value="What do you want to buy? "/>
        What do you want to buy? 
      </td>
    </tr>
    <tr>
      <td>
        <select name="os0">
          <option value="One question">
            One question €8.50 EUR
          </option>
          <option value="Two question + energy reading">
            Two question + energy reading €17.00 EUR
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
  <input type="hidden" name="currency_code" value="EUR" />
  <input type="image" src="https://www.paypalobjects.com/en_US/i/btn/btn_buynowCC_LG.gif" border="0" name="submit" title="PayPal - The safer, easier way to pay online!" alt="Buy Now" />
</form>-->
                
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



    
    
    
<button id="affiliateTipButton" type="button" class="btn btn-danger" data-bs-toggle="modal" data-bs-target="#affiliatePricingModal" style="display: none;">
        <i class="bi bi-globe"></i> <img src="https://flagcdn.com/24x18/in.png" alt="India">  <img src="https://flagpedia.net/data/org/w1160/au.webp" style="width:24px;height:18px;" alt="Africa Union"> Tarot Reading 
    </button></span>
</div>


<style>
.profile-container {
  position: relative;
  width: 100%;
  max-width: 800px; 
  margin: 0 auto;
}

.cover-image img {
  width: 100%;
  height: auto;
  border-top-left-radius: 8px;
  border-top-right-radius: 8px;
}

.profile-image img {
  position: absolute;
  bottom: -50px; 
  left: 10%;
  transform: translateX(-50%);
  width: 100px; 
  height: 100px; 
  border: 4px solid #fff;
  border-radius: 50%;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
}
</style>

<br/>

<div class="language-plaintext highlighter-rouge">
  {% for collection in site.collections reversed %}
    {% assign collection_name = collection.label %}
    
    {% if collection_name == 'posts' %}
    
      {% assign latest_post = nil %}
    
      {% for post in site[collection_name] %}
        {% if latest_post == nil or post.date > latest_post.date %}
          {% assign latest_post = post %}
        {% endif %}
      {% endfor %}
      
     <div style="border: 1px solid #5c0120; border-radius: 10px; box-shadow: 0 0 10px rgba(45, 55, 72, 1); margin-bottom: 3px; padding: 2px;">
        
          {% if latest_post %}
            <b><a href="{{ latest_post.url }}">🌟 Last update: {{ latest_post.date | date: "%Y-%m-%d" }}</a></b>
          {% else %}
            <p>No posts found in the {{ collection_name }} collection.</p>
          {% endif %}
       
      </div>
    
    {% endif %}
  {% endfor %}
</div> 

<h4><i class="bi bi-bell"></i>    
 <a class="btn btn-white btn-outline-secondary float-end" data-bs-toggle="modal" data-bs-target="#duckModal"><i class="bi bi-bookmarks"></i></a>
</h4>


{{page.description}}


<div class="modal fade" id="duckModal" tabindex="-1" role="dialog" aria-labelledby="duckModalLabel" aria-hidden="true"> <div class="modal-dialog" role="document"> <div class="modal-content"> <div class="modal-header"> <h5 class="modal-title" id="duckModalLabel"> <i class="bi bi-bookmarks"></i> Info</h5> </div> 
    
<div class="modal-body"> <img src="" class="img-fluid" />
  
  This blog contains topic on spirituality, tarot, oracles, dreams, self-improvement and conspiracy theories; the other two blog links are in sidebar - Updates and Diary.  

<style>
    .bookmark-container {
        max-width: 600px;
        margin: auto;
    }
    .bookmark {
        background: #181821;
        padding: 15px;
        border-radius: 10px;
        margin-bottom: 15px;
        display: flex;
        flex-direction: column;
        position: relative;
        font-size: 0.8em;
    }
    .author {
        display: flex;
        align-items: center;
        margin-bottom: 10px;
    }
    .author img {
        width: 80px;
        height: 80px;
        border-radius: 50%;
        margin-right: 5px;
    }
    .author a {
        color: #1da1f2;
        text-decoration: none;
        font-weight: bold;
    }
    .author-description {
        font-size: 0.8em;
        color: gray;
        margin-top: 5px;
        font-weight: lighter;
    }
    .date {
        font-size: 0.8em;
        color: gray;
      margin-left: auto!important;
    }
    .link-icon {
        position: absolute;
        bottom: 10px;
        right: 10px;
        font-size: 1.2em;
    }
    .link-icon a {
        color: gray;
        text-decoration: none;
    }
    .link-icon a:hover {
        color: #1da1f2;
    }
</style>

<div id="bookmarks" class="bookmark-container"></div>




</div> 
    
    
<div class="modal-footer"> <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button> </div> </div> </div> </div>


<style>
  .search-result {
    margin-bottom: 20px;
  }

  .img-fluid {
    max-width: 100%;
    height: auto;
  }

  .highlight {
    background-color: yellow;
    color: red;
  }

  #result-count {
    margin-top: 10px;
    font-weight: bold;
    border-bottom: 1px solid #ccc;
    padding-bottom: 5px;
  }
</style>

<label for="search-box">Search</label>
<input type="text" id="search-box" name="query">
<button class="btn btn-secondary" id="clear-search" onclick="clearSearch()">Clear</button> 
<div id="result-count"></div>
<ul id="search-results"></ul>

<script>
  document.addEventListener('DOMContentLoaded', function () {
    var searchBox = document.getElementById('search-box');
    var searchResults = document.getElementById('search-results');
    var resultCount = document.getElementById('result-count');

    document.getElementById('clear-search').addEventListener('click', function () {
      searchBox.value = '';
      searchResults.innerHTML = '';
    });

    searchBox.addEventListener('input', function () {
      var query = this.value.trim().toLowerCase();

      if (query.length > 2) {
        search(query);
      } else {
        renderResults([]);
      }
    });

    function search(query) {
      var xhr = new XMLHttpRequest();
      xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 && xhr.status == 200) {
          var parser = new DOMParser();
          var xml = parser.parseFromString(xhr.responseText, 'application/xml');
          var items = xml.getElementsByTagName('item');
          var results = [];

          for (var i = 0; i < items.length; i++) {
            var title = items[i].getElementsByTagName('title')[0].textContent;
            var link = items[i].getElementsByTagName('link')[0].textContent;
            var contentNode = items[i].getElementsByTagName('description')[0];
            var content = new XMLSerializer().serializeToString(contentNode);

            if (title.toLowerCase().includes(query) || content.toLowerCase().includes(query)) {
              results.push({ title: title, url: link, content: content });
            }
          }

          renderResults(results, query);
        }
      };

      xhr.open('GET', '/feed.xml', true);
      xhr.send();
    }

    function renderResults(results, query) {
      searchResults.innerHTML = '';

      if (results.length > 0) {
        resultCount.textContent = results.length + ' result(s) found.';
        results.forEach(function (result) {
          var listItem = document.createElement('li');
          listItem.className = 'search-result';

          var link = document.createElement('a');
          link.href = result.url;
          link.textContent = result.title;

          var contentDiv = document.createElement('div');
          contentDiv.innerHTML = result.content;

          highlightSearchTerm(contentDiv, query);

          listItem.appendChild(link);
         
          searchResults.appendChild(listItem);
        });
      } else {
        resultCount.textContent = 'No results found.';
      }
    }

    function highlightSearchTerm(element, query) {
      var regex = new RegExp(query, 'ig');
      var content = element.innerHTML;

      element.innerHTML = content.replace(regex, function (match) {
        return '<span class="highlight">' + match + '</span>';
      });
    }

    function clearSearch() {
      searchBox.value = '';
      searchResults.innerHTML = '';
    }
  });
</script>

