# Assignment A5: Practical/Applied Task - Responsive Portfolio Website
**Student Name:** Maria Santos
**Student ID:** 2024-CS-4762
**Date:** March 22, 2026

---

## index.html

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Portafolio - My Portfolio</title>
    <link rel="stylesheet" href="estilos.css">
</head>
<body>
    <!-- Navigation / Navegación -->
    <nav class="navbar">
        <div class="logo">Portfolio</div>
        <ul class="nav-links">
            <li><a href="#home">Inicio / Home</a></li>
            <li><a href="#about">Acerca / About</a></li>
            <li><a href="#skills">Habilidades / Skills</a></li>
            <li><a href="#projects">Proyectos / Projects</a></li>
            <li><a href="#contact">Contacto / Contact</a></li>
        </ul>
    </nav>

    <!-- Hero Section / Sección Principal -->
    <section id="home" class="hero">
        <h1>Hola, soy <span class="highlight">Maria Santos</span></h1>
        <h1>Hello, I'm <span class="highlight">Maria Santos</span></h1>
        <p>Développeuse Web Full-Stack</p>
        <p>Full-Stack Web Developer</p>
        <button class="cta-button">Ver mi trabajo / View My Work</button>
    </section>

    <!-- About Section / Sección Acerca de Mí -->
    <section id="about" class="about-section">
        <h2>Sobre Mí / About Me</h2>
        <div class="about-content">
            <p>
                Soy una desarrolladora web apasionada con experiencia en crear
                aplicaciones modernas y responsives. Je parle trois langues et
                je peux travailler with teams internationales.
            </p>
            <p>
                I have experience con HTML5, CSS3, JavaScript, React, y muchas
                otras technologies modernas. Mi objetivo est créer beautiful et
                functional websites que los usuarios adoran.
            </p>
        </div>
    </section>

    <!-- Skills Section / Sección de Habilidades -->
    <section id="skills" class="skills-section">
        <h2>Mis Habilidades / My Skills</h2>
        <div class="skills-grid">
            <div class="skill-card">
                <h3>HTML5</h3>
                <div class="skill-bar">
                    <div class="skill-progress" style="width: 90%">90%</div>
                </div>
            </div>
            <div class="skill-card">
                <h3>CSS3</h3>
                <div class="barre-de-compétence">
                    <div class="progress" style="width: 85%">85%</div>
                </div>
            </div>
            <div class="skill-card">
                <h3>JavaScript</h3>
                <div class="skill-bar">
                    <div class="skill-progress" style="width: 80%">80%</div>
                </div>
            </div>
            <div class="skill-card">
                <h3>React.js</h3>
                <div class="skill-bar">
                    <div class="skill-progress" style="width: 75%">75%</div>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section / Sección de Proyectos -->
    <section id="projects" class="projects-section">
        <h2>Proyectos Destacados / Featured Projects</h2>
        <div class="projects-grid">
            <article class="project-card">
                <h3>Site E-Commerce</h3>
                <p>
                    Una tienda en línea complète avec panier d'achats,
                    payment integration, et admin dashboard.
                </p>
                <div class="project-tags">
                    <span>React</span>
                    <span>Node.js</span>
                    <span>MongoDB</span>
                </div>
                <a href="#" class="project-link">Ver Proyecto / View Project</a>
            </article>

            <article class="project-card">
                <h3>Application de Tâches</h3>
                <p>
                    Task management app con funciones de collaboration
                    et actualizaciones en temps réel.
                </p>
                <div class="project-tags">
                    <span>Vue.js</span>
                    <span>Firebase</span>
                    <span>CSS3</span>
                </div>
                <a href="#" class="project-link">Ver Demo / View Demo</a>
            </article>

            <article class="project-card">
                <h3>Portfolio Personnel</h3>
                <p>
                    Mi sitio web personal showcasing all mis proyectos
                    et compétences as web developer.
                </p>
                <div class="project-tags">
                    <span>HTML5</span>
                    <span>CSS3</span>
                    <span>JavaScript</span>
                </div>
                <a href="#" class="project-link">Visiter / Visit</a>
            </article>
        </div>
    </section>

    <!-- Contact Section / Sección de Contacto -->
    <section id="contact" class="contact-section">
        <h2>Contáctame / Contact Me / Contactez-moi</h2>
        <form class="contact-form">
            <div class="form-group">
                <label for="nombre">Nombre / Name / Nom:</label>
                <input type="text" id="nombre" name="name" required>
            </div>
            <div class="form-group">
                <label for="correo">Email / Correo electrónico:</label>
                <input type="email" id="correo" name="email" required>
            </div>
            <div class="form-group">
                <label for="mensaje">Mensaje / Message:</label>
                <textarea id="mensaje" name="message" rows="5" required></textarea>
            </div>
            <button type="submit">Enviar / Send / Envoyer</button>
        </form>
    </section>

    <!-- Footer / Pie de Página -->
    <footer class="footer">
        <p>&copy; 2026 Maria Santos. Todos los derechos reservados / All rights reserved / Tous droits réservés</p>
        <div class="social-links">
            <a href="#">GitHub</a>
            <a href="#">LinkedIn</a>
            <a href="#">Twitter</a>
        </div>
    </footer>

    <script src="script.js"></script>
</body>
</html>
```

## estilos.css

```css
/* Reset y Estilos Básicos */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Arial', sans-serif;
    line-height: 1.6;
    color: #333;
}

/* Navigation / Navegación */
.navbar {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    padding: 1rem 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo {
    color: white;
    font-size: 1.5rem;
    font-weight: bold;
}

.nav-links {
    display: flex;
    list-style: none;
    gap: 2rem;
}

.nav-links a {
    color: white;
    text-decoration: none;
    transition: opacity 0.3s;
}

.nav-links a:hover {
    opacity: 0.8;
}

/* Hero Section / Sección Hero */
.hero {
    min-height: 100vh;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    padding: 2rem;
}

.hero h1 {
    font-size: 3rem;
    margin-bottom: 1rem;
}

.highlight {
    color: #ffd700;
}

.cta-button {
    background: white;
    color: #667eea;
    padding: 1rem 2rem;
    border: none;
    border-radius: 50px;
    font-size: 1.1rem;
    cursor: pointer;
    margin-top: 2rem;
    transition: transform 0.3s;
}

.cta-button:hover {
    transform: translateY(-3px);
}

/* About Section / Acerca */
.about-section {
    padding: 5rem 2rem;
    max-width: 1200px;
    margin: 0 auto;
}

.about-section h2 {
    text-align: center;
    font-size: 2.5rem;
    margin-bottom: 2rem;
}

.about-content p {
    font-size: 1.1rem;
    margin-bottom: 1.5rem;
    text-align: center;
}

/* Skills Section / Habilidades */
.skills-section {
    background: #f8f9fa;
    padding: 5rem 2rem;
}

.skills-section h2 {
    text-align: center;
    font-size: 2.5rem;
    margin-bottom: 3rem;
}

.skills-grid {
    max-width: 1200px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 2rem;
}

.skill-card {
    background: white;
    padding: 2rem;
    border-radius: 10px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

.skill-bar,
.barre-de-compétence {
    background: #e0e0e0;
    border-radius: 10px;
    overflow: hidden;
    margin-top: 1rem;
}

.skill-progress,
.progress {
    background: linear-gradient(90deg, #667eea, #764ba2);
    color: white;
    padding: 0.5rem;
    text-align: center;
    font-weight: bold;
    transition: width 1s ease;
}

/* Projects Section / Proyectos */
.projects-section {
    padding: 5rem 2rem;
    max-width: 1200px;
    margin: 0 auto;
}

.projects-section h2 {
    text-align: center;
    font-size: 2.5rem;
    margin-bottom: 3rem;
}

.projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
}

.project-card {
    background: white;
    padding: 2rem;
    border-radius: 10px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    transition: transform 0.3s;
}

.project-card:hover {
    transform: translateY(-10px);
}

.project-tags {
    display: flex;
    gap: 0.5rem;
    margin: 1rem 0;
}

.project-tags span {
    background: #e0e0e0;
    padding: 0.3rem 0.8rem;
    border-radius: 20px;
    font-size: 0.9rem;
}

.project-link {
    color: #667eea;
    text-decoration: none;
    font-weight: bold;
}

/* Contact Section / Contacto */
.contact-section {
    background: #f8f9fa;
    padding: 5rem 2rem;
}

.contact-section h2 {
    text-align: center;
    font-size: 2.5rem;
    margin-bottom: 3rem;
}

.contact-form {
    max-width: 600px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
}

.form-group {
    display: flex;
    flex-direction: column;
}

.form-group label {
    margin-bottom: 0.5rem;
    font-weight: bold;
}

.form-group input,
.form-group textarea {
    padding: 0.8rem;
    border: 2px solid #e0e0e0;
    border-radius: 5px;
    font-family: inherit;
}

.contact-form button {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 1rem;
    border: none;
    border-radius: 5px;
    font-size: 1.1rem;
    cursor: pointer;
    transition: opacity 0.3s;
}

.contact-form button:hover {
    opacity: 0.9;
}

/* Footer / Pie de página */
.footer {
    background: #333;
    color: white;
    padding: 2rem;
    text-align: center;
}

.social-links {
    margin-top: 1rem;
    display: flex;
    justify-content: center;
    gap: 2rem;
}

.social-links a {
    color: white;
    text-decoration: none;
}

/* Responsive Design / Diseño Responsivo */
@media (max-width: 768px) {
    .nav-links {
        flex-direction: column;
        gap: 1rem;
    }

    .hero h1 {
        font-size: 2rem;
    }

    .projects-grid,
    .skills-grid {
        grid-template-columns: 1fr;
    }
}
```

## script.js

```javascript
// Smooth scrolling pour navigation / para navegación
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function(e) {
        e.preventDefault();
        const target = document.querySelector(this.getAttribute('href'));
        target.scrollIntoView({
            behavior: 'smooth'
        });
    });
});

// Animación de barras de habilidades / Animation des barres de compétence
const observador = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            const skillBars = entry.target.querySelectorAll('.skill-progress, .progress');
            skillBars.forEach(bar => {
                const width = bar.style.width;
                bar.style.width = '0%';
                setTimeout(() => {
                    bar.style.width = width;
                }, 100);
            });
        }
    });
});

const skillsSection = document.querySelector('.skills-section');
if (skillsSection) {
    observador.observe(skillsSection);
}

// Form handling / Manejo de formulario / Gestion du formulaire
const contactForm = document.querySelector('.contact-form');
contactForm.addEventListener('submit', (e) => {
    e.preventDefault();

    const formData = new FormData(contactForm);
    console.log('Formulaire soumis:', Object.fromEntries(formData));

    alert('¡Gracias por tu mensaje! / Thank you for your message! / Merci pour votre message!');
    contactForm.reset();
});
```

---

## Notas / Notes

Este portafolio está diseñado en tres idiomas / This portfolio is designed in three languages / Ce portfolio est conçu en trois langues:
- Español
- English
- Français

Características / Features / Caractéristiques:
- Design responsive
- Smooth scrolling
- Animaciones en scroll
- Formulario de contacto
- Multi-langue support

---
