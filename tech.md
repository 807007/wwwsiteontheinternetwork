---
title: Tech portfolio
permalink: /portfolio/tech/
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
Welcome to the portfolio for all my tech projects, school and personal.

My [grade 11 LED cube logic project](./LEDcubelogic/) is a good showcase of my skills in circuit design.

My [custom LLM instructions](./LLMI1/) are a good resource for learning how to use AI more effectively for reasoning tasks.
