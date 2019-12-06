---
layout: default
nav: true
order: 3
---

<center>

<h1>Search Teach-Gerry</h1>
<p></p>
</center>

<!-- Html Elements for Search -->
<div id="search-container">
    <center><input type="text" id="search-input" placeholder="search..."></center>
    <ul id="results-container"></ul>
</div>

<!-- Script pointing to search-script.js -->
<script src="src/search.js" type="text/javascript"></script>

<!-- Configuration -->
<script>
    SimpleJekyllSearch({
      searchInput: document.getElementById('search-input'),
      resultsContainer: document.getElementById('results-container'),
      searchResultTemplate: '<li><h3><a href="{url}">{title}: <span class="postdate">{authors} | {date}</span></a></h3></li>',
      json: 'search.json',
      limit: 15,
    })
</script>

