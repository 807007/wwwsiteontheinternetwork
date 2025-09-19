---
title: Welcome to Kaden LeBlanc's world wide website on the inter-network
---
About me
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
I'm a student taking CS (intro to CS) and TER (robotics and control systems).

While most people choose to list their current interests, or maybe even their interests over time, my interests follow a well-defined pattern:

I'm a creativity-minded person who likes applying the mindset to highly logical tasks.

This leads me to have an interest in certain kinds of design, complex strategy games that reward thinking outside of the box, and an interest in AI.

[Here](./portfolio/) you'll find my portfolio for CS and TER (shortened to course code for convenience).

When I find the time, I'll try to post my personal projects here as well.
