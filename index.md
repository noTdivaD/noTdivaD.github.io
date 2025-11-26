---
layout: default
title: Accueil
---

<div class="card floating">
  <h2>Bienvenue !</h2>
  <p>Découvrez mes projets réalisés sur Unity et mes expériences dans la création de jeux vidéo et d’applications 3D & VR.</p>
</div>

<!-- Diaporama -->
<div class="slideshow-container">

  <div class="slide fade">
    <img src="noTdivaD.github.io/assets/images/GTA6/GTA6_1.png" style="width:100%">
    <div class="text">Grandma Throwing Apocalypse 6</div>
  </div>

  <div class="slide fade">
    <img src="noTdivaD.github.io/assets/images/CinemachineProject/CinePro_1.png" style="width:100%">
    <div class="text">CinemachineProject</div>
  </div>

  <div class="slide fade">  
    <img src="noTdivaD.github.io/assets/images/ShopSimulator/ShopSim_4.png" style="width:100%">
    <div class="text">Shop Simulator</div>
  </div>

  <div class="slide fade">
    <img src="noTdivaD.github.io/assets/images/palevoyage.jpg" style="width:100%">
    <div class="text">The Pale Voyage</div>
  </div>

</div>

<script>
  let slideIndex = 0;
  showSlides();

  function showSlides() {
    let i;
    let slides = document.getElementsByClassName("slide");
    for (i = 0; i < slides.length; i++) {
      slides[i].style.display = "none";
    }
    slideIndex++;
    if (slideIndex > slides.length) {slideIndex = 1}
    slides[slideIndex-1].style.display = "block";
    setTimeout(showSlides, 4000); // Change toutes les 4s
  }
</script>