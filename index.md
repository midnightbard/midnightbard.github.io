--- 
title: Midnight Bard
layout: home
image: 
description:  
category: diary
media: spiritual
---

<div class="profile-container">
  <div class="cover-image">
    <img src="/pictures/cover.jpeg" alt="Cover Image">
  </div>
  <div class="profile-image">
    <img src="/pictures/mb.png" alt="Profile Image">
    
    
    
    
    
  </div>
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
          listItem.appendChild(contentDiv);
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

