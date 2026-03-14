---
title: Main Page
permalink: /en/Main_Page
redirect_from:
    - "/"
    - "/en"
published: true
---

<div id="intro-screen">
<div class="intro-content">
<img src="{{ '/wiki/image/logo.png' | relative_url }}" class="intro-logo">
<h1>ACM Devil Medical</h1>
<p>Bienvenido al manual médico</p>
</div>
</div>

<script>
window.addEventListener("load", function() {
    const intro = document.getElementById("intro-screen");

    setTimeout(() => {
        intro.style.opacity = "0";
        setTimeout(() => intro.remove(), 1000);
    }, 2000);
});
</script>
