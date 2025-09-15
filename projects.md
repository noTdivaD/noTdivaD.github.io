---
layout: default
title: Projets
---

<div class="card floating">
  <h2>Mes projets</h2>
  <p>Quelques projets réalisés lors de ma formation à Simplon Sud...</p>
</div>

<div class="projects-grid">
  {% for project in site.data.projects %}
    <div class="showcase">
      <h3>{{ project.icon }} {{ project.title }}</h3>
      <div class="showcase-media">
        {% for media in project.media %}
          {% if media.type == "image" %}
            <img src="{{ media.src }}" alt="{{ project.title }} Screenshot">
          {% elsif media.type == "slideshow" %}
            <div class="slideshow">
              {% for img in media.src %}
                <div class="slide fade">
                  <img src="{{ img }}" alt="{{ project.title }} Screenshot">
                </div>
              {% endfor %}
              <a class="prev" onclick="plusSlides(-1)">❮</a>
              <a class="next" onclick="plusSlides(1)">❯</a>
            </div>
            <div class="dots">
              {% for img in media.src %}
                <span class="dot" onclick="currentSlide({{ forloop.index }})"></span>
              {% endfor %}
            </div>
          {% elsif media.type == "video" %}
            <video controls>
              <source src="{{ media.src }}" type="video/mp4">
            </video>
          {% endif %}
        {% endfor %}
      </div>
      <p>
        {{ project.description | markdownify }}<br>
        <strong>Durée :</strong> {{ project.duration }}.<br>
        <strong>Équipe :</strong>
        {% for member in project.team %}
          <a href="{{ member.link }}">{{ member.name }}</a>{% if forloop.last == false %}, {% endif %}
        {% endfor %}
      </p>
      {% if project.download %}
        <a class="button" href="{{ project.download }}" download>⬇ Télécharger</a>
      {% endif %}
    </div>
  {% endfor %}
</div>

