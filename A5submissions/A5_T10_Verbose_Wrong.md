# Assignment A5: Practical/Applied Task - Responsive Portfolio Website
**Student Name:** Christopher Davis
**Student ID:** 2024-CS-5493
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
    <style>
        /* I think inline styles might be okay for this? Not sure if I should use
           a separate CSS file or not. I've seen both approaches and I'm not entirely
           certain which is better. Some people say separate files are better for
           organization, but then you have to link them and that's another HTTP request,
           though I guess browsers cache CSS files so maybe it doesn't matter much.

           Anyway, here are my styles: */

        body {
            font-family: Arial, sans-serif; /* Arial is pretty standard, right? */
            margin: 0;
            padding: 0;
        }

        nav {
            background-color: #333; /* Dark gray, or is it grey? I never remember */
            padding: 20px;
        }

        nav a {
            color: white;
            text-decoration: none;
            margin-right: 20px; /* Or should this be margin-left? */
        }

        .hero {
            background-color: lightblue; /* Maybe I should use a hex code? */
            padding: 100px 20px;
            text-align: center;
        }

        .section {
            padding: 50px 20px;
            /* I'm not sure if this is enough padding */
        }
    </style>
</head>
<body>
    <!-- Navigation bar - I hope this works on mobile -->
    <nav>
        <a href="#home">Home</a>
        <a href="#about">About</a>
        <a href="#projects">Projects</a>
        <a href="#contact">Contact</a>
        <!-- Should I add more links? -->
    </nav>

    <!-- Hero section, though I'm not entirely sure what makes a section "hero" -->
    <div class="hero" id="home">
        <h1>Welcome to My Portfolio</h1>
        <p>I'm a web developer (I think)</p>
        <!-- Should there be a button here? Many portfolios have buttons -->
    </div>

    <!-- About section -->
    <div class="section" id="about">
        <h2>About Me</h2>
        <p>
            I'm interested in web development and I know HTML and CSS, and a bit
            of JavaScript though I'm still learning it. I've made a few websites
            before but I'm not sure if they count as real projects or just practice.
            This portfolio itself is kind of a project I guess.
        </p>
        <!-- Is this too much text or not enough? -->
    </div>

    <!-- Projects section -->
    <div class="section" id="projects">
        <h2>My Projects</h2>
        <!-- I should probably make this look better with cards or something -->
        <div>
            <h3>Project 1</h3>
            <p>A website I made. It has HTML and CSS.</p>
            <!-- Should I include screenshots? I didn't add any -->
        </div>
        <div>
            <h3>Project 2</h3>
            <p>Another website. This one has some JavaScript too.</p>
            <!-- Maybe I should link to these projects? But they're not online -->
        </div>
    </div>

    <!-- Contact section -->
    <div class="section" id="contact">
        <h2>Contact Me</h2>
        <form>
            <!-- I'm not sure how to actually make this form work -->
            <input type="text" placeholder="Your Name">
            <!-- Should I add a label? I've seen it both ways -->
            <input type="email" placeholder="Your Email">
            <textarea placeholder="Message"></textarea>
            <!-- Is placeholder text enough or do I need labels for accessibility? -->
            <button type="submit">Send</button>
            <!-- This button doesn't actually do anything yet -->
        </form>
    </div>

    <script>
        // Some JavaScript I guess

        // I wanted to add smooth scrolling but I'm not completely sure how
        // I found this code online and I think it works:
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                // This preventDefault() stops the default behavior, I think?
                const target = document.querySelector(this.getAttribute('href'));
                if (target) { // Should I check if target exists? Probably safer
                    target.scrollIntoView({
                        behavior: 'smooth'
                        // There's also block and inline options but I'm not using them
                    });
                }
            });
        });

        // Form handling - this just shows an alert for now
        // In a real website this would send an email or store the data somehow
        const form = document.querySelector('form');
        form.addEventListener('submit', function(e) {
            e.preventDefault(); // Stop the form from actually submitting
            alert('Form submitted! (Not really though)');
            // I should probably validate the inputs but I'm not sure how
        });

        // Maybe I should add more JavaScript? But what would it do?
    </script>
</body>
</html>
```

---

## Notes

This portfolio is pretty basic. I included:

1. A navigation bar (though it might not work great on mobile, I'm not sure)
2. Different sections for home, about, projects, and contact
3. A form (it doesn't actually work though)
4. Some JavaScript for smooth scrolling
5. Inline CSS (maybe I should have used a separate file?)

Things I'm uncertain about:
- Whether the design is responsive enough
- If I should have used more semantic HTML
- Whether inline styles are okay or if I needed a separate CSS file
- If the JavaScript actually works properly (it seemed to when I tested it)
- Whether I need more projects or if two is okay
- If the form needs proper labels for accessibility
- Whether the color scheme is professional enough

I tried to follow best practices but I'm not completely confident about what those are. The website loads and the navigation works, so I think the core functionality is there, but it could probably be improved in many ways that I'm not entirely sure about.

---
