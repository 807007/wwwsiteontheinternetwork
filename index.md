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
I'm a student taking CS (intro to CS) and TER (computer engineering, robotics and control systems).

While most people choose to list their current interests, or maybe even their interests over time, my interests follow a well-defined pattern: <br>
I'm a creativity-minded person who likes applying the mindset to highly logical tasks. <br>
This leads me to have an interest in certain kinds of design, complex strategy games that reward thinking outside of the box, and an interest in machine learning.

[Here](./portfolio/) you can navigate to my CS and TER portfolios (shortened to course code for convenience). <br>
When I find the time, I'll try to post my personal projects here as well.

Personal e-mail: kadenleblanc2123@gmail.com <br>
You'd think I would have more to put here, but e-mail is all I've got.
