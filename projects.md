---
layout: default
title: Projets
---

<div class="card floating"> 
  <h2>Mes projets</h2>
  <p>
    Quelques projets réalisés lors de ma formation à Simplon Sud. 
    La plupart sont des <span class="highlight">démonstrations de faisabilité</span> 
    pour explorer des fonctionnalités de <span class="highlight">Unity</span>.  
    On retrouve par exemple :
  </p>
  <ul>
    <li><strong>Grandma Throwing Apocalypse 6</strong> – Jeu 3D où l'on contrôle une grand-mère propulsée en enfer. Travail sur les interfaces et le changement de scènes. Réalisé en une semaine avec <a href="https://www.linkedin.com/in/pataki-nandor-9b809735b/">Pataki Nandor</a> et <a href="https://www.linkedin.com/in/mohammad-jawad-07ab93259/">Mohammad Jawad</a>.</li>
    <li><strong>CinemachineProject</strong> – Démonstration 3D sur les caméras, shaders et instanciations de préfabs. Réalisé en deux jours.</li>
    <li><strong>Shop Simulator</strong> – Jeu de gestion de commerce. Développement de la logique clients, du système de vente et de la ville. Réalisé en trois semaines avec <a href="https://www.linkedin.com/in/niels-carre-360907333/">Niels Carré</a> et <a href="https://www.linkedin.com/in/layla-el-bakali-taheri-59ba4435a/">Layla El Bakali Taheri</a>.</li>
    <li><strong>The Pale Voyage</strong> – Prototype expérimental en 3D & VR (Unity XR). Travail sur l’implémentation VR, shaders HLSL, LOD et pooling. Réalisé en deux semaines.</li>
  </ul>
</div>

<div class="projects-grid">
{% for project in site.data.projects %}
  <div class="showcase">
    <h3>{{ project.icon }} {{ project.title }}</h3>
    <div class="showcase-media">

      {% for media in project.media %}
          {% if media.type == "slideshow" %}

            {% assign ss_id = project.title | slugify | append: "-" | append: forloop.index0 %}

            <div class="slideshow" data-slideshow="{{ ss_id }}">
              {% for img in media.src %}
                <div class="slide fade">
                  <img src="{{ img }}" alt="{{ project.title }} Screenshot">
                </div>
              {% endfor %}
              <a class="prev" onclick="plusSlides(-1, '{{ ss_id }}')">❮</a>
              <a class="next" onclick="plusSlides(1, '{{ ss_id }}')">❯</a>
            </div>

            <div class="dots" data-dots="{{ ss_id }}">
              {% for img in media.src %}
                <span class="dot" onclick="currentSlide({{ forloop.index }}, '{{ ss_id }}')"></span>
              {% endfor %}
            </div>

          {% endif %}
        {% endfor %}
    </div>

    <p>
      {{ project.description | markdownify }}<br>
      <strong>Durée :</strong> {{ project.duration }}.<br>
      <strong>Équipe :</strong>
      {% for member in project.team %}
        <a href="{{ member.link }}">{{ member.name }}</a>{% unless forloop.last %}, {% endunless %}
      {% endfor %}
    </p>

    {% if project.download %}
      <a class="button" href="{{ project.download }}" download>⬇ Télécharger</a>
    {% endif %}
  </div>
{% endfor %}
</div>

<script>
// Store current slide index per slideshow
const slideIndex = {};

document.addEventListener("DOMContentLoaded", () => {
  document.querySelectorAll(".slideshow").forEach(slideshow => {
    slideshow.dataset.index = 1;
    showSlides(slideshow, 1);
  });
});

function plusSlides(btn, n) {
  const slideshow = btn.closest(".showcase").querySelector(".slideshow");
  slideshow.dataset.index = Number(slideshow.dataset.index) + n;
  showSlides(slideshow);
}

function currentSlide(dot, n) {
  const showcase = dot.closest(".showcase");
  const slideshow = showcase.querySelector(".slideshow");
  slideshow.dataset.index = n;
  showSlides(slideshow);
}

function showSlides(slideshow) {
  const slides = slideshow.querySelectorAll(".slide");
  const dots = slideshow
    .closest(".showcase")
    .querySelectorAll(".dot");

  let index = Number(slideshow.dataset.index);

  if (index > slides.length) index = 1;
  if (index < 1) index = slides.length;

  slideshow.dataset.index = index;

  slides.forEach(s => s.style.display = "none");
  dots.forEach(d => d.classList.remove("active"));

  slides[index - 1].style.display = "block";
  dots[index - 1].classList.add("active");
}
</script>
