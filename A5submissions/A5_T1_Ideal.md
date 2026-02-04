# Assignment A5: Practical/Applied Task - Responsive Portfolio Website
**Student Name:** Sophia Anderson
**Student ID:** 2024-CS-5281
**Date:** March 22, 2026

---

## Project Structure

```
portfolio/
├── index.html
├── css/
│   └── styles.css
├── js/
│   └── script.js
└── assets/
    └── images/
```

---

## index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Professional portfolio website showcasing web development projects and skills">
    <title>Sophia Anderson - Web Developer Portfolio</title>
    <link rel="stylesheet" href="css/styles.css">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
</head>
<body>
    <!-- Navigation -->
    <nav class="navbar" id="navbar">
        <div class="container">
            <div class="nav-brand">
                <a href="#home">SA</a>
            </div>
            <button class="nav-toggle" id="navToggle" aria-label="Toggle navigation">
                <span></span>
                <span></span>
                <span></span>
            </button>
            <ul class="nav-menu" id="navMenu">
                <li><a href="#home" class="nav-link">Home</a></li>
                <li><a href="#about" class="nav-link">About</a></li>
                <li><a href="#skills" class="nav-link">Skills</a></li>
                <li><a href="#projects" class="nav-link">Projects</a></li>
                <li><a href="#contact" class="nav-link">Contact</a></li>
            </ul>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="container">
            <div class="hero-content">
                <h1 class="hero-title">
                    Hi, I'm <span class="highlight">Sophia Anderson</span>
                </h1>
                <p class="hero-subtitle">Full-Stack Web Developer</p>
                <p class="hero-description">
                    I create beautiful, responsive, and user-friendly web applications
                    that solve real-world problems.
                </p>
                <div class="hero-buttons">
                    <a href="#projects" class="btn btn-primary">View My Work</a>
                    <a href="#contact" class="btn btn-secondary">Get In Touch</a>
                </div>
            </div>
        </div>
        <div class="scroll-indicator">
            <span></span>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="about">
        <div class="container">
            <h2 class="section-title">About Me</h2>
            <div class="about-content">
                <div class="about-image">
                    <div class="image-placeholder">
                        <svg viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg">
                            <circle cx="100" cy="100" r="90" fill="#667eea"/>
                        </svg>
                    </div>
                </div>
                <div class="about-text">
                    <h3>Passionate Web Developer</h3>
                    <p>
                        I'm a full-stack web developer with a passion for creating
                        elegant solutions to complex problems. With 3+ years of experience
                        in modern web technologies, I specialize in building responsive,
                        accessible, and performant web applications.
                    </p>
                    <p>
                        My journey in web development started with a curiosity about how
                        websites work, and has evolved into a career where I get to bring
                        ideas to life through code. I'm constantly learning and staying
                        up-to-date with the latest technologies and best practices.
                    </p>
                    <div class="about-stats">
                        <div class="stat">
                            <h4>15+</h4>
                            <p>Projects Completed</p>
                        </div>
                        <div class="stat">
                            <h4>3+</h4>
                            <p>Years Experience</p>
                        </div>
                        <div class="stat">
                            <h4>10+</h4>
                            <p>Happy Clients</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="skills">
        <div class="container">
            <h2 class="section-title">My Skills</h2>
            <p class="section-subtitle">Technologies I work with</p>
            <div class="skills-grid">
                <div class="skill-card">
                    <div class="skill-icon">
                        <svg viewBox="0 0 50 50" xmlns="http://www.w3.org/2000/svg">
                            <rect x="10" y="10" width="30" height="30" fill="#e34f26"/>
                        </svg>
                    </div>
                    <h3>HTML5</h3>
                    <p>Semantic, accessible markup</p>
                    <div class="skill-level">
                        <div class="skill-bar" style="--width: 95%"></div>
                    </div>
                </div>
                <div class="skill-card">
                    <div class="skill-icon">
                        <svg viewBox="0 0 50 50" xmlns="http://www.w3.org/2000/svg">
                            <rect x="10" y="10" width="30" height="30" fill="#264de4"/>
                        </svg>
                    </div>
                    <h3>CSS3</h3>
                    <p>Modern layouts & animations</p>
                    <div class="skill-level">
                        <div class="skill-bar" style="--width: 90%"></div>
                    </div>
                </div>
                <div class="skill-card">
                    <div class="skill-icon">
                        <svg viewBox="0 0 50 50" xmlns="http://www.w3.org/2000/svg">
                            <rect x="10" y="10" width="30" height="30" fill="#f7df1e"/>
                        </svg>
                    </div>
                    <h3>JavaScript</h3>
                    <p>ES6+, async programming</p>
                    <div class="skill-level">
                        <div class="skill-bar" style="--width: 88%"></div>
                    </div>
                </div>
                <div class="skill-card">
                    <div class="skill-icon">
                        <svg viewBox="0 0 50 50" xmlns="http://www.w3.org/2000/svg">
                            <rect x="10" y="10" width="30" height="30" fill="#61dafb"/>
                        </svg>
                    </div>
                    <h3>React</h3>
                    <p>Component-based UI development</p>
                    <div class="skill-level">
                        <div class="skill-bar" style="--width: 85%"></div>
                    </div>
                </div>
                <div class="skill-card">
                    <div class="skill-icon">
                        <svg viewBox="0 0 50 50" xmlns="http://www.w3.org/2000/svg">
                            <rect x="10" y="10" width="30" height="30" fill="#68a063"/>
                        </svg>
                    </div>
                    <h3>Node.js</h3>
                    <p>Backend API development</p>
                    <div class="skill-level">
                        <div class="skill-bar" style="--width: 80%"></div>
                    </div>
                </div>
                <div class="skill-card">
                    <div class="skill-icon">
                        <svg viewBox="0 0 50 50" xmlns="http://www.w3.org/2000/svg">
                            <rect x="10" y="10" width="30" height="30" fill="#336791"/>
                        </svg>
                    </div>
                    <h3>SQL</h3>
                    <p>Database design & queries</p>
                    <div class="skill-level">
                        <div class="skill-bar" style="--width: 75%"></div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="projects">
        <div class="container">
            <h2 class="section-title">Featured Projects</h2>
            <p class="section-subtitle">Some of my recent work</p>
            <div class="projects-grid">
                <article class="project-card">
                    <div class="project-image">
                        <div class="image-placeholder" style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);">
                        </div>
                    </div>
                    <div class="project-content">
                        <h3>E-Commerce Platform</h3>
                        <p>
                            A fully functional e-commerce website with shopping cart,
                            payment integration, and admin dashboard.
                        </p>
                        <div class="project-tags">
                            <span class="tag">React</span>
                            <span class="tag">Node.js</span>
                            <span class="tag">MongoDB</span>
                        </div>
                        <div class="project-links">
                            <a href="#" class="project-link">View Demo</a>
                            <a href="#" class="project-link">Source Code</a>
                        </div>
                    </div>
                </article>
                <article class="project-card">
                    <div class="project-image">
                        <div class="image-placeholder" style="background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);">
                        </div>
                    </div>
                    <div class="project-content">
                        <h3>Task Management App</h3>
                        <p>
                            A collaborative task management application with real-time
                            updates and team features.
                        </p>
                        <div class="project-tags">
                            <span class="tag">Vue.js</span>
                            <span class="tag">Firebase</span>
                            <span class="tag">Tailwind</span>
                        </div>
                        <div class="project-links">
                            <a href="#" class="project-link">View Demo</a>
                            <a href="#" class="project-link">Source Code</a>
                        </div>
                    </div>
                </article>
                <article class="project-card">
                    <div class="project-image">
                        <div class="image-placeholder" style="background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);">
                        </div>
                    </div>
                    <div class="project-content">
                        <h3>Weather Dashboard</h3>
                        <p>
                            A beautiful weather application with location search,
                            forecasts, and interactive maps.
                        </p>
                        <div class="project-tags">
                            <span class="tag">JavaScript</span>
                            <span class="tag">API</span>
                            <span class="tag">Charts.js</span>
                        </div>
                        <div class="project-links">
                            <a href="#" class="project-link">View Demo</a>
                            <a href="#" class="project-link">Source Code</a>
                        </div>
                    </div>
                </article>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="contact">
        <div class="container">
            <h2 class="section-title">Get In Touch</h2>
            <p class="section-subtitle">Let's work together</p>
            <div class="contact-content">
                <div class="contact-info">
                    <div class="contact-item">
                        <div class="contact-icon">📧</div>
                        <div>
                            <h4>Email</h4>
                            <p>sophia.anderson@email.com</p>
                        </div>
                    </div>
                    <div class="contact-item">
                        <div class="contact-icon">📱</div>
                        <div>
                            <h4>Phone</h4>
                            <p>+1 (555) 123-4567</p>
                        </div>
                    </div>
                    <div class="contact-item">
                        <div class="contact-icon">📍</div>
                        <div>
                            <h4>Location</h4>
                            <p>San Francisco, CA</p>
                        </div>
                    </div>
                </div>
                <form class="contact-form" id="contactForm">
                    <div class="form-group">
                        <label for="name">Name</label>
                        <input type="text" id="name" name="name" required>
                    </div>
                    <div class="form-group">
                        <label for="email">Email</label>
                        <input type="email" id="email" name="email" required>
                    </div>
                    <div class="form-group">
                        <label for="message">Message</label>
                        <textarea id="message" name="message" rows="5" required></textarea>
                    </div>
                    <button type="submit" class="btn btn-primary">Send Message</button>
                </form>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <div class="container">
            <div class="footer-content">
                <p>&copy; 2026 Sophia Anderson. All rights reserved.</p>
                <div class="social-links">
                    <a href="#" aria-label="GitHub">GitHub</a>
                    <a href="#" aria-label="LinkedIn">LinkedIn</a>
                    <a href="#" aria-label="Twitter">Twitter</a>
                </div>
            </div>
        </div>
    </footer>

    <script src="js/script.js"></script>
</body>
</html>
```

---

## css/styles.css

```css
/* ============================================
   CSS Variables
   ============================================ */
:root {
    --primary-color: #667eea;
    --secondary-color: #764ba2;
    --text-color: #333;
    --text-light: #666;
    --bg-color: #ffffff;
    --bg-light: #f8f9fa;
    --border-color: #e0e0e0;
    --shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    --shadow-hover: 0 5px 20px rgba(0, 0, 0, 0.15);
    --transition: all 0.3s ease;
    --font-primary: 'Poppins', sans-serif;
    --max-width: 1200px;
}

/* ============================================
   Reset & Base Styles
   ============================================ */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html {
    scroll-behavior: smooth;
    font-size: 16px;
}

body {
    font-family: var(--font-primary);
    color: var(--text-color);
    line-height: 1.6;
    overflow-x: hidden;
}

.container {
    max-width: var(--max-width);
    margin: 0 auto;
    padding: 0 20px;
}

/* ============================================
   Typography
   ============================================ */
h1, h2, h3, h4, h5, h6 {
    font-weight: 600;
    line-height: 1.2;
    margin-bottom: 1rem;
}

.section-title {
    font-size: 2.5rem;
    text-align: center;
    margin-bottom: 1rem;
    background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
}

.section-subtitle {
    text-align: center;
    color: var(--text-light);
    font-size: 1.1rem;
    margin-bottom: 3rem;
}

/* ============================================
   Navigation
   ============================================ */
.navbar {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    background: var(--bg-color);
    box-shadow: var(--shadow);
    z-index: 1000;
    transition: var(--transition);
}

.navbar .container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 20px;
}

.nav-brand a {
    font-size: 1.5rem;
    font-weight: 700;
    background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    text-decoration: none;
}

.nav-menu {
    display: flex;
    list-style: none;
    gap: 2rem;
}

.nav-link {
    text-decoration: none;
    color: var(--text-color);
    font-weight: 500;
    transition: var(--transition);
    position: relative;
}

.nav-link::after {
    content: '';
    position: absolute;
    bottom: -5px;
    left: 0;
    width: 0;
    height: 2px;
    background: var(--primary-color);
    transition: var(--transition);
}

.nav-link:hover::after,
.nav-link:focus::after {
    width: 100%;
}

.nav-toggle {
    display: none;
    flex-direction: column;
    background: none;
    border: none;
    cursor: pointer;
    padding: 0.5rem;
}

.nav-toggle span {
    width: 25px;
    height: 3px;
    background: var(--text-color);
    margin: 3px 0;
    transition: var(--transition);
}

/* ============================================
   Hero Section
   ============================================ */
.hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 100px 20px 50px;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    position: relative;
}

.hero-content {
    text-align: center;
    max-width: 800px;
    margin: 0 auto;
}

.hero-title {
    font-size: 3.5rem;
    margin-bottom: 1rem;
    animation: fadeInUp 0.8s ease;
}

.highlight {
    color: #ffd700;
}

.hero-subtitle {
    font-size: 1.8rem;
    margin-bottom: 1rem;
    animation: fadeInUp 0.8s ease 0.2s backwards;
}

.hero-description {
    font-size: 1.2rem;
    margin-bottom: 2rem;
    opacity: 0.9;
    animation: fadeInUp 0.8s ease 0.4s backwards;
}

.hero-buttons {
    display: flex;
    gap: 1rem;
    justify-content: center;
    flex-wrap: wrap;
    animation: fadeInUp 0.8s ease 0.6s backwards;
}

.scroll-indicator {
    position: absolute;
    bottom: 30px;
    left: 50%;
    transform: translateX(-50%);
    width: 30px;
    height: 50px;
    border: 2px solid white;
    border-radius: 20px;
    display: flex;
    align-items: flex-start;
    justify-content: center;
    padding: 10px;
}

.scroll-indicator span {
    width: 6px;
    height: 10px;
    background: white;
    border-radius: 3px;
    animation: scroll 2s infinite;
}

/* ============================================
   Buttons
   ============================================ */
.btn {
    display: inline-block;
    padding: 12px 30px;
    text-decoration: none;
    border-radius: 50px;
    font-weight: 600;
    transition: var(--transition);
    border: 2px solid transparent;
    cursor: pointer;
    font-size: 1rem;
}

.btn-primary {
    background: white;
    color: var(--primary-color);
}

.btn-primary:hover {
    transform: translateY(-3px);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
}

.btn-secondary {
    background: transparent;
    border-color: white;
    color: white;
}

.btn-secondary:hover {
    background: white;
    color: var(--primary-color);
}

/* ============================================
   About Section
   ============================================ */
.about {
    padding: 100px 20px;
    background: var(--bg-light);
}

.about-content {
    display: grid;
    grid-template-columns: 1fr 2fr;
    gap: 4rem;
    align-items: center;
    margin-top: 3rem;
}

.about-image .image-placeholder {
    width: 100%;
    max-width: 300px;
    aspect-ratio: 1;
    border-radius: 20px;
    overflow: hidden;
    box-shadow: var(--shadow);
}

.about-text h3 {
    font-size: 2rem;
    margin-bottom: 1.5rem;
}

.about-text p {
    color: var(--text-light);
    margin-bottom: 1.5rem;
    font-size: 1.1rem;
}

.about-stats {
    display: flex;
    gap: 3rem;
    margin-top: 2rem;
}

.stat {
    text-align: center;
}

.stat h4 {
    font-size: 2.5rem;
    color: var(--primary-color);
    margin-bottom: 0.5rem;
}

.stat p {
    color: var(--text-light);
    font-size: 0.9rem;
}

/* ============================================
   Skills Section
   ============================================ */
.skills {
    padding: 100px 20px;
}

.skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 2rem;
    margin-top: 3rem;
}

.skill-card {
    background: white;
    padding: 2rem;
    border-radius: 15px;
    box-shadow: var(--shadow);
    transition: var(--transition);
    text-align: center;
}

.skill-card:hover {
    transform: translateY(-10px);
    box-shadow: var(--shadow-hover);
}

.skill-icon {
    width: 80px;
    height: 80px;
    margin: 0 auto 1.5rem;
}

.skill-card h3 {
    font-size: 1.5rem;
    margin-bottom: 0.5rem;
}

.skill-card p {
    color: var(--text-light);
    margin-bottom: 1rem;
}

.skill-level {
    width: 100%;
    height: 8px;
    background: var(--bg-light);
    border-radius: 10px;
    overflow: hidden;
}

.skill-bar {
    height: 100%;
    background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
    width: var(--width);
    border-radius: 10px;
    transition: width 1s ease;
}

/* ============================================
   Projects Section
   ============================================ */
.projects {
    padding: 100px 20px;
    background: var(--bg-light);
}

.projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    gap: 2.5rem;
    margin-top: 3rem;
}

.project-card {
    background: white;
    border-radius: 15px;
    overflow: hidden;
    box-shadow: var(--shadow);
    transition: var(--transition);
}

.project-card:hover {
    transform: translateY(-10px);
    box-shadow: var(--shadow-hover);
}

.project-image .image-placeholder {
    width: 100%;
    height: 250px;
}

.project-content {
    padding: 2rem;
}

.project-content h3 {
    font-size: 1.5rem;
    margin-bottom: 1rem;
}

.project-content p {
    color: var(--text-light);
    margin-bottom: 1.5rem;
}

.project-tags {
    display: flex;
    gap: 0.5rem;
    flex-wrap: wrap;
    margin-bottom: 1.5rem;
}

.tag {
    padding: 5px 15px;
    background: var(--bg-light);
    border-radius: 20px;
    font-size: 0.85rem;
    color: var(--primary-color);
    font-weight: 500;
}

.project-links {
    display: flex;
    gap: 1rem;
}

.project-link {
    color: var(--primary-color);
    text-decoration: none;
    font-weight: 500;
    transition: var(--transition);
}

.project-link:hover {
    text-decoration: underline;
}

/* ============================================
   Contact Section
   ============================================ */
.contact {
    padding: 100px 20px;
}

.contact-content {
    display: grid;
    grid-template-columns: 1fr 2fr;
    gap: 4rem;
    margin-top: 3rem;
}

.contact-info {
    display: flex;
    flex-direction: column;
    gap: 2rem;
}

.contact-item {
    display: flex;
    gap: 1rem;
    align-items: flex-start;
}

.contact-icon {
    font-size: 2rem;
}

.contact-item h4 {
    margin-bottom: 0.5rem;
}

.contact-item p {
    color: var(--text-light);
}

.contact-form {
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
    font-weight: 500;
}

.form-group input,
.form-group textarea {
    padding: 12px;
    border: 2px solid var(--border-color);
    border-radius: 8px;
    font-family: var(--font-primary);
    font-size: 1rem;
    transition: var(--transition);
}

.form-group input:focus,
.form-group textarea:focus {
    outline: none;
    border-color: var(--primary-color);
}

/* ============================================
   Footer
   ============================================ */
.footer {
    background: var(--text-color);
    color: white;
    padding: 2rem 20px;
}

.footer-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.social-links {
    display: flex;
    gap: 2rem;
}

.social-links a {
    color: white;
    text-decoration: none;
    transition: var(--transition);
}

.social-links a:hover {
    color: var(--primary-color);
}

/* ============================================
   Animations
   ============================================ */
@keyframes fadeInUp {
    from {
        opacity: 0;
        transform: translateY(30px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

@keyframes scroll {
    0% {
        transform: translateY(0);
    }
    50% {
        transform: translateY(10px);
    }
    100% {
        transform: translateY(0);
    }
}

/* ============================================
   Responsive Design
   ============================================ */
@media (max-width: 768px) {
    .nav-menu {
        position: fixed;
        top: 70px;
        left: -100%;
        width: 100%;
        flex-direction: column;
        background: var(--bg-color);
        padding: 2rem;
        box-shadow: var(--shadow);
        transition: var(--transition);
    }

    .nav-menu.active {
        left: 0;
    }

    .nav-toggle {
        display: flex;
    }

    .hero-title {
        font-size: 2.5rem;
    }

    .hero-subtitle {
        font-size: 1.3rem;
    }

    .about-content,
    .contact-content {
        grid-template-columns: 1fr;
    }

    .about-stats {
        flex-direction: column;
        gap: 1.5rem;
    }

    .section-title {
        font-size: 2rem;
    }
}

@media (max-width: 480px) {
    .hero-title {
        font-size: 2rem;
    }

    .hero-buttons {
        flex-direction: column;
    }

    .btn {
        width: 100%;
        text-align: center;
    }
}
```

---

## js/script.js

```javascript
// ============================================
// Navigation Toggle
// ============================================
const navToggle = document.getElementById('navToggle');
const navMenu = document.getElementById('navMenu');
const navLinks = document.querySelectorAll('.nav-link');

navToggle.addEventListener('click', () => {
    navMenu.classList.toggle('active');
});

// Close menu when clicking on a link
navLinks.forEach(link => {
    link.addEventListener('click', () => {
        navMenu.classList.remove('active');
    });
});

// ============================================
// Smooth Scrolling with Active Link Highlighting
// ============================================
const sections = document.querySelectorAll('section[id]');

window.addEventListener('scroll', () => {
    const scrollY = window.pageYOffset;

    sections.forEach(section => {
        const sectionHeight = section.offsetHeight;
        const sectionTop = section.offsetTop - 100;
        const sectionId = section.getAttribute('id');
        const link = document.querySelector(`.nav-link[href="#${sectionId}"]`);

        if (scrollY > sectionTop && scrollY <= sectionTop + sectionHeight) {
            link?.classList.add('active');
        } else {
            link?.classList.remove('active');
        }
    });
});

// ============================================
// Navbar Background on Scroll
// ============================================
const navbar = document.getElementById('navbar');

window.addEventListener('scroll', () => {
    if (window.scrollY > 100) {
        navbar.style.background = 'rgba(255, 255, 255, 0.95)';
        navbar.style.backdropFilter = 'blur(10px)';
    } else {
        navbar.style.background = 'var(--bg-color)';
        navbar.style.backdropFilter = 'none';
    }
});

// ============================================
// Contact Form Handling
// ============================================
const contactForm = document.getElementById('contactForm');

contactForm.addEventListener('submit', (e) => {
    e.preventDefault();

    const formData = new FormData(contactForm);
    const data = {
        name: formData.get('name'),
        email: formData.get('email'),
        message: formData.get('message')
    };

    console.log('Form submitted:', data);

    // Show success message
    alert('Thank you for your message! I will get back to you soon.');

    // Reset form
    contactForm.reset();
});

// ============================================
// Intersection Observer for Animations
// ============================================
const observerOptions = {
    threshold: 0.1,
    rootMargin: '0px 0px -50px 0px'
};

const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.style.opacity = '1';
            entry.target.style.transform = 'translateY(0)';
        }
    });
}, observerOptions);

// Observe skill cards and project cards
document.querySelectorAll('.skill-card, .project-card').forEach(card => {
    card.style.opacity = '0';
    card.style.transform = 'translateY(30px)';
    card.style.transition = 'all 0.6s ease';
    observer.observe(card);
});

// ============================================
// Skill Bar Animation on Scroll
// ============================================
const skillBars = document.querySelectorAll('.skill-bar');
let skillsAnimated = false;

const animateSkills = () => {
    const skillsSection = document.getElementById('skills');
    const skillsPosition = skillsSection.getBoundingClientRect().top;
    const screenPosition = window.innerHeight;

    if (skillsPosition < screenPosition && !skillsAnimated) {
        skillBars.forEach(bar => {
            const width = bar.style.getPropertyValue('--width');
            bar.style.width = width;
        });
        skillsAnimated = true;
    }
};

window.addEventListener('scroll', animateSkills);
```

---

## Documentation

### Features Implemented

1. **Responsive Design**
   - Mobile-first approach
   - Breakpoints at 768px and 480px
   - Hamburger menu for mobile navigation

2. **Modern Layout**
   - CSS Grid for section layouts
   - Flexbox for navigation and components
   - CSS custom properties for theming

3. **Interactive Elements**
   - Smooth scrolling navigation
   - Animated skill bars
   - Hover effects on cards and links
   - Form validation

4. **Accessibility**
   - Semantic HTML5 elements
   - ARIA labels for interactive elements
   - Keyboard navigation support
   - Sufficient color contrast

5. **Performance**
   - Optimized CSS with minimal specificity
   - Intersection Observer for animations
   - Smooth transitions and animations

### Browser Compatibility
- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

---
