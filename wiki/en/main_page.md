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
    <img src="/spanishac/wiki/image/logo.png" class="intro-logo">

    <h1>ACM Devil Medical</h1>
    <p>Bienvenido al manual médico</p>

    <button id="enter-button">Entrar</button>
  </div>
</div>

<script>
document.addEventListener("DOMContentLoaded", function(){

  const intro = document.getElementById("intro-screen");
  const button = document.getElementById("enter-button");

  if(localStorage.getItem("introSeen")){
      intro.style.display = "none";
      return;
  }

  button.addEventListener("click", function(){

      intro.style.opacity = "0";

      setTimeout(() => {
          intro.remove();
      }, 800);

      localStorage.setItem("introSeen", true);

  });

});
</script>
