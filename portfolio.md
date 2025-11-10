---
title: Portfolio selector
permalink: /portfolio/
---
Choose a portfolio
---
<button onclick="updatePage()">Update to latest deployment</button>

<script>
function updatePage() {
    // Get the current URL without query params, then append a random one
    const baseUrl = window.location.origin + window.location.pathname;
    const cacheBuster = '?v=' + new Date().getTime(); // Timestamp ensures uniqueness
    window.location.href = baseUrl + cacheBuster;
}
</script>
[Go to Tech portfolio](./tech/)

[Go to CS portfolio](./cs/)
