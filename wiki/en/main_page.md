---
title: Main Page
permalink: /en/Main_Page
layout: default
---

<div id="intro-screen">
<div class="intro-content">

<img src="{{ '/wiki/image/logo.png' | relative_url }}" class="intro-logo">

<h1 class="intro-title">ACM Devil Medical</h1>
<p class="intro-text">Bienvenido al manual médico</p>

<button id="enter-button">ENTER MANUAL</button>

</div>
</div>

<script>
document.addEventListener("DOMContentLoaded", function() {

const intro = document.getElementById("intro-screen");
const button = document.getElementById("enter-button");

button.addEventListener("click", function(){

intro.style.opacity = "0";

setTimeout(function(){
intro.style.display = "none";
}, 800);

});

});
</script>
