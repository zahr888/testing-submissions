# Assignment A5: Practical/Applied Task - Responsive Portfolio Website
**Student Name:** Jordan Taylor
**Student ID:** 2024-CS-3918
**Date:** March 22, 2026

---

## index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portfolio Website</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <nav>
            <ul>
                <li><a href="#home">Home</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#projects">Projects</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </nav>
    </header>

    <section id="home" class="hero">
        <h1>Welcome to My Portfolio</h1>
        <p>Web Developer & Designer</p>
        <a href="#contact" class="btn">Get In Touch</a>
    </section>

    <section id="about">
        <h2>About Me</h2>
        <p>
            I'm a passionate web developer with experience in creating
            responsive and user-friendly websites.
        </p>
    </section>

    <section id="projects">
        <h2>My Projects</h2>
        <div class="project-grid">
            <div class="project-card">
                <h3>E-Commerce Site</h3>
                <p>A fully functional online store built with React</p>
            </div>
            <div class="project-card">
                <h3>Blog Platform</h3>
                <p>Content management system with user authentication</p>
            </div>
        </div>
    </section>

    <section id="contact">
        <h2>Contact Me</h2>
        <form id="contactForm">
            <input type="text" placeholder="Name" required>
            <input type="email" placeholder="Email" required>
            <textarea placeholder="Message" required></textarea>
