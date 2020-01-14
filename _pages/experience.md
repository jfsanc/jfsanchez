---
title: Sobre mi
customJS: ["loadFullRepoData"]
permalink: /experience/
---

<img src="C:\Users\EQUIPO\Documents\GitHub\jfsanchez.pw\assets\img\profile-photo.png" style="zoom:75%;" />

{% include banner.html heading="Sobre mi" content="El Marketing hace parte de mi gestión profesional, me gusta enseñar, leer libros y escribir, aprendí desarrollo y estadística en aplicación con el lenguaje Python 🐍." %}

<section id="projects" class="section">
    {% include headingWithImage.html h="Proyectos" lvl=2 img="/assets/img/folder.png" alt="📁" %}
    <div id="project-grid" class="card-grid">
        <!-- Projects get populated here dynamically (see index.js) -->
        <div id="project-placeholder" class="project">
            <header>
                <p><strong>¿Quieres ver más de mi trabajo?</strong></p>
            </header>
            <div>
                <p>Mira mis otros repositorios:</p>
                <a href="https://github.com/jfsanc">{% include svg.html svg="github" %}</a>
            </div>
        </div>
    </div>
</section>
<section id="skills" class="section">
    {% include headingWithImage.html h="Destrezas y Habilidades" lvl=2 img="/assets/img/juggler.png" alt="🤹" %}
    <div id="skill-grid">
        {% for skill in site.data.skills %}
        <div>
            <h3 class="skill-category">{{ skill.category }}</h3>
            {% for item in skill.items %}
            <div class="skill-item">
                <span class="skill-name">{{ item.name }}</span>
                <div class="skill-rating">
                    {% for i in (1..item.rating) %}
                    {% include svg.html svg="star" class="star star-filled" %}
                    {% endfor %}
                    {% assign j = item.rating | plus: 1 %}
                    {% for i in (j..5) %}
                    {% include svg.html svg="star" class="star star-empty" %}
                    {% endfor %}
                    {% assign rating = '' %}
                    {% if item.rating == 1 %}{% assign rating = 'Familiar' %}
                    {% elsif item.rating == 2 %}{% assign rating = 'Basic' %}
                    {% elsif item.rating == 3 %}{% assign rating = 'Intermediate' %}
                    {% elsif item.rating == 4 %}{% assign rating = 'Competent' %}
                    {% elsif item.rating == 5 %}{% assign rating = 'Advanced' %}
                    {% endif %}
                    {% include tooltip.html position='top' text=rating %}
                </div>
            </div>
            {% endfor %}
        </div>
        {% endfor %}
    </div>
</section>
<section id="work" class="section">
    {% include headingWithImage.html h="Experiencia Laboral" lvl=2 img="/assets/img/briefcase.png" alt="💼" %}
    <section class="card-grid">
    {% for job in site.data.work %}
        <section class="job">
            <header>
                <h3 class="job-title">{{ job.title }}, {{ job.company }}</h3>
                <p class="date-range">{{ job.dateRange }}</p>
            </header>
            <ul class="responsibilities" >
                {% for responsibility in job.responsibilities %}
                <li>{{ responsibility }}</li>
                {% endfor %}
            </ul>
            <footer class="technologies-used">
                {% for tech in job.tech %}
                <div class="tech {{tech}}">{{tech}}</div>
                {% endfor %}
            </footer>
        </section>
    {% endfor %}
    </section>
</section>
<section id="education" class="section">
    {% include headingWithImage.html h="Educación" lvl=2 img="/assets/img/graduation-cap.png" alt="🎓" %}
    {% for institution in site.data.education %}
    <div class="institution collapsible">
        <div class="collapsible-header">
            {% include svg.html svg="angle-down" %}
            <span>
                <strong>{{ institution.name }}<br></strong>
                {{ institution.degree }}<br>
                {{ institution.gpa }} GPA, {{ institution.years }}
            </span>
        </div>
        <div class="collapsible-content">
            <div class="courses">
                <h3><em>Perfil Ocupacional</em></h3>
                <ul>
                    {% for course in institution.courses %}
                    <li>{{ course }}</li>
                    {% endfor %}
                </ul>
            </div>
            <div class="awards">
                <h3><em>Premios y reconocimientos</em></h3>
                <ul>
                    {% for award in institution.awards %}
                    <li>{{ award }}</li>
                    {% endfor %}
                </ul>
            </div>
        </div>
    </div>
    {% endfor %}
</section>

<!-- Currently only used on this page -->
<script src="/assets/scripts/collapsible.js"></script>
