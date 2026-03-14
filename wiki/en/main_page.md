---
title: Página Inicio
permalink: /en/Main_Page
layout: default
---

## ACM

Bienvenido al manual del **Advanced Combat Medicine (ACM)**.

Este manual recoge los procedimientos médicos tácticos utilizados en el sistema **ACM Prometeo**, basado en los principios de **Tactical Combat Casualty Care (TCCC)**.

Aquí encontrarás:

- Protocolos médicos (MARCH / TCCC)
- Uso del equipamiento médico
- Procedimientos de tratamiento
- Funciones médicas del sistema

<div id="intro-screen">
<div class="intro-content">

<img src="{{ '/wiki/image/logo.png' | relative_url }}" class="intro-logo">

<h1 class="intro-title">ACM Sistema Médico Prometeo</h1>
<p class="intro-text">Bienvenido al manual médico</p>

<button id="enter-button">ENTER MANUAL</button>

</div>
</div>

<script>
function enterManual() {

const intro = document.getElementById("intro-screen");

intro.style.transition = "opacity 0.8s ease";
intro.style.opacity = "0";

setTimeout(function(){
intro.style.display = "none";
},800);

}

document.getElementById("enter-button").onclick = enterManual;
</script>
