# Assignment A5: Practical/Applied Task - Responsive Portfolio Website
**Student Name:** Michael Thompson
**Student ID:** 2024-CS-6394
**Date:** March 22, 2026

---

## index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Portfolio</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <nav>
        <a href="#home">Home</a>
        <a href="#about">About</a>
        <a href="#projects">Projects</a>
        <a href="#contact">Contact</a>
    </nav>

    <section id="home">
        <h1>John Doe</h1>
        <p>Web Developer</p>
    </section>

    <section id="about">
        <h2>About Me</h2>
        <p>I'm a web developer with experience in HTML, CSS, and JavaScript.</p>
    </section>

    <section id="projects">
        <h2>My Projects</h2>
        <div class="project">
            <h3>Project 1</h3>
            <p>A cool website</p>
        </div>
        <div class="project">
            <h3>Project 2</h3>
            <p>Another website</p>
        </div>
    </section>

    <section id="contact">
        <h2>Contact</h2>
        <form>
            <input type="text" placeholder="Name">
            <input type="email" placeholder="Email">
            <textarea placeholder="Message"></textarea>
            <button>Send</button>
        </form>
    </section>

    <script src="script.js"></script>
</body>
</html>
```

## style.css

```css
* {
    margin: 0;
    padding: 0;
}

body {
    font-family: Arial;
}

nav {
    background: #333;
    padding: 20px;
}

nav a {
    color: white;
    margin-right: 20px;
    text-decoration: none;
}

section {
    padding: 50px;
    min-height: 400px;
}

#home {
    background: lightblue;
    text-align: center;
}

.project {
    border: 1px solid #ccc;
    padding: 20px;
    margin: 10px;
}

form input,
form textarea {
    display: block;
    width: 300px;
    margin: 10px 0;
    padding: 10px;
}

button {
    padding: 10px 20px;
    background: #333;
    color: white;
    border: none;
}

/* Some responsive stuff */
@media (max-width: 600px) {
    nav a {
        display: block;
        margin: 10px 0;
    }
}
```

## script.js

```javascript
// Smooth scrolling
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function(e) {
        e.preventDefault();
        document.querySelector(this.getAttribute('href')).scrollIntoView({
            behavior: 'smooth'
        });
    });
});

// Form submission
document.querySelector('form').addEventListener('submit', function(e) {
    e.preventDefault();
    alert('Message sent!');
});
```

---

## Notes

The website is functional but pretty basic. It has:
- Navigation that works
- Sections for content
- A form (though it doesn't actually send anything)
- Some mobile responsiveness
- Smooth scrolling

Could definitely use more styling and better layout.

---
