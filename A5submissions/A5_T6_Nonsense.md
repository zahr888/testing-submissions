# Assignment A5: Practical/Applied Task - Responsive Portfolio Website
**Student Name:** Tyler Brooks
**Student ID:** 2024-CS-1374
**Date:** March 22, 2026

---

## index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🎭 Quantum Portfolio Experience 🎭</title>
    <link rel="stylesheet" href="chaos.css">
</head>
<body onload="initializeChaos()">
    <!-- Navigation that defies the laws of physics -->
    <nav id="quantumNav" style="position: absolute; top: ???px; left: ???px;">
        <a href="#void">Home (Maybe)</a>
        <a href="#existential">About (Who am I?)</a>
        <a href="#impossible">Projects (They don't exist)</a>
        <a href="#screaming">Contact (Into the void)</a>
    </nav>

    <!-- Hero section that's actually a villain -->
    <section id="hero" style="transform: rotate(???deg);">
        <h1 id="nameDisplay">Loading name from parallel universe...</h1>
        <p class="profession">Quantum Web Destroyer | Reality Bender</p>
        <button onclick="randomizeReality()">Click if you dare</button>
        <div id="floatingEmojis">🦄🌈🔥💀🎪🎨🎭🎪</div>
    </section>

    <!-- About section that lies -->
    <section id="about" style="visibility: sometimes;">
        <h2>About Me (Probably)</h2>
        <p id="aboutText">
            I am <span id="randomJob"></span> who specializes in
            <span id="randomSkill"></span>. My favorite color is
            <span id="randomColor"></span> and I can code in
            <span id="randomLang"></span>.
        </p>
        <img src="data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw=="
             alt="Me (or am I?)" width="???" height="???">
    </section>

    <!-- Skills that don't make sense -->
    <section id="skills">
        <h2>My Superpowers</h2>
        <ul>
            <li>HTML (Hyper Text Markup Llama) - 900% proficiency</li>
            <li>CSS (Chaotic Style Screaming) - Mastery level: Purple</li>
            <li>JavaScript (Just Another Very Another Script) - Speed: Backwards</li>
            <li>React (Really Eating All Code Today) - Version: ∞.β.🦄</li>
            <li>Quantum Computing - Can run Schrödinger's code (works and doesn't work simultaneously)</li>
            <li>Time Travel Debugging - Fix bugs before they happen</li>
            <li>Telepathic UI/UX - Users think it and it appears (sometimes)</li>
        </ul>
    </section>

    <!-- Projects from alternate dimensions -->
    <section id="projects">
        <h2>Projects That May Or May Not Exist</h2>

        <div class="project" style="border: ???px dashed rainbow;">
            <h3>🌀 The Infinite Loop Website</h3>
            <p>A website that loads itself forever. Powered by recursion and existential dread.</p>
            <p><strong>Technologies:</strong> HTML∞, CSS-1, JavaScript.undefined</p>
            <a href="javascript:void(while(true){})">Visit Site (Don't)</a>
        </div>

        <div class="project" style="transform: matrix3d(???);">
            <h3>🎲 Random Everything App</h3>
            <p>Every refresh gives you a completely different website. No two visits are the same.
               In fact, it might not even be a website.</p>
            <p><strong>Technologies:</strong> Math.random() × ∞, Chaos Theory, String Theory</p>
            <a href="javascript:location.reload()">Try Your Luck</a>
        </div>

        <div class="project" style="opacity: 0.5; filter: blur(???px);">
            <h3>👻 Ghost Social Network</h3>
            <p>A social network for ghosts. Users are invisible. Messages disappear before being sent.
               Friend requests go to void. Perfect privacy!</p>
            <p><strong>Technologies:</strong> Vue.js (Vanishing User Experience), Node.ghost(), MongoDB.boo</p>
            <a href="#nowhere">Join Now (You can't)</a>
        </div>

        <div class="project" style="animation: wobble ???s infinite;">
            <h3>🎨 CSS Art Gallery (No CSS)</h3>
            <p>A gallery of CSS art created without using any CSS. Pure HTML inline styles that shouldn't work but do.</p>
            <p><strong>Technologies:</strong> HTML style="" attributes, Determination, Madness</p>
            <a href="data:text/html,<h1 style='color:random'>ART</h1>">View Gallery</a>
        </div>

        <div class="project" style="font-family: 'Comic Sans MS', 'Papyrus', cursive;">
            <h3>⏰ Time Travel Blog</h3>
            <p>Blog posts from the past, present, and future. Sometimes posts appear before they're written.
               Paradoxes are considered features.</p>
            <p><strong>Technologies:</strong> Temporal JavaScript, 4D CSS, HTML5.future</p>
            <a href="javascript:alert('This blog will be created yesterday')">Read Blog</a>
        </div>
    </section>

    <!-- Skills visualization using ASCII art because why not -->
    <section id="skills-chart">
        <h2>Skills Represented As ASCII Art</h2>
        <pre>
    HTML    [████████████████████] 187%
    CSS     [███████▓▓▓░░░░░░░░░░] ???%
    JS      [▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒] NaN%
    React   [🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥] 🔥
    PHP     [💀💀💀💀💀💀💀💀💀💀] RIP
        </pre>
    </section>

    <!-- Contact form that doesn't contact anyone -->
    <section id="contact">
        <h2>Contact Me (Messages Go To The Void)</h2>
        <form onsubmit="return sendToVoid(event)">
            <label for="name">Name (Any name, real or imaginary):</label>
            <input type="text" id="name" value="John Doe #42" required>

            <label for="email">Email (We won't read it):</label>
            <input type="email" id="email" value="example@void.null" required>

            <label for="message">Message:</label>
            <textarea id="message" rows="4" required>
Hello from the other side...
            </textarea>

            <button type="submit">Send Into Void</button>
            <button type="button" onclick="randomizeForm()">Randomize Everything</button>
        </form>
        <p id="formResponse"></p>
    </section>

    <!-- Footer that's actually a header -->
    <footer style="position: fixed; top: 0; bottom: auto;">
        <p>© <span id="year"></span> Quantum Portfolio | All rights reversed |
           <a href="javascript:document.body.innerHTML=''">Delete Everything</a>
        </p>
    </footer>

    <!-- Floating random elements -->
    <div id="floatingElements"></div>

    <script src="madness.js"></script>
    <script>
        // Initialize chaos
        function initializeChaos() {
            console.log("Welcome to the chaos");

            // Random year
            document.getElementById('year').textContent = Math.floor(Math.random() * 3000);

            // Random name
            const names = ["Schrödinger's Cat", "The Developer", "Nobody", "Everybody", "Error 404"];
            document.getElementById('nameDisplay').textContent =
                names[Math.floor(Math.random() * names.length)];

            // Random job, skill, color, language
            const jobs = ["time traveler", "ghost whisperer", "professional procrastinator", "meme archeologist"];
            const skills = ["breaking the internet", "creating bugs", "turning coffee into code", "staring at screens"];
            const colors = ["invisible", "ultraviolet", "negative green", "quantum blue"];
            const langs = ["Binary Spoken Word", "Emoji++", "LOLCODE", "Brainfuck"];

            document.getElementById('randomJob').textContent = jobs[Math.floor(Math.random() * jobs.length)];
            document.getElementById('randomSkill').textContent = skills[Math.floor(Math.random() * skills.length)];
            document.getElementById('randomColor').textContent = colors[Math.floor(Math.random() * colors.length)];
            document.getElementById('randomLang').textContent = langs[Math.floor(Math.random() * langs.length)];

            // Random background color every second
            setInterval(() => {
                document.body.style.background = `hsl(${Math.random() * 360}, 70%, 80%)`;
            }, 1000);

            // Spawn floating emojis
            setInterval(spawnFloatingEmoji, 500);
        }

        function randomizeReality() {
            document.body.style.transform = `rotate(${Math.random() * 360}deg)`;
            alert("Reality has been randomized. Good luck!");
            location.reload();
        }

        function sendToVoid(event) {
            event.preventDefault();
            const responses = [
                "Message sent to /dev/null",
                "Your message was intercepted by aliens",
                "Message delivered to parallel universe",
                "Error: Recipient doesn't exist",
                "Message consumed by the void",
                "Success! (Just kidding, nothing was sent)"
            ];
            document.getElementById('formResponse').textContent =
                responses[Math.floor(Math.random() * responses.length)];
            return false;
        }

        function randomizeForm() {
            document.getElementById('name').value = "User" + Math.floor(Math.random() * 9999);
            document.getElementById('email').value = Math.random().toString(36) + "@example.com";
            document.getElementById('message').value = "Lorem ipsum dolor sit " +
                Math.random().toString(36).substr(2);
        }

        function spawnFloatingEmoji() {
            const emojis = ['🦄', '🌈', '🔥', '💀', '👻', '🎪', '🎭', '🎨', '🚀', '✨', '💩', '🤡'];
            const emoji = document.createElement('div');
            emoji.textContent = emojis[Math.floor(Math.random() * emojis.length)];
            emoji.style.position = 'fixed';
            emoji.style.left = Math.random() * window.innerWidth + 'px';
            emoji.style.top = Math.random() * window.innerHeight + 'px';
            emoji.style.fontSize = (Math.random() * 50 + 20) + 'px';
            emoji.style.zIndex = '9999';
            emoji.style.pointerEvents = 'none';
            emoji.style.animation = `float ${Math.random() * 5 + 3}s ease-in-out infinite`;
            document.body.appendChild(emoji);

            setTimeout(() => emoji.remove(), 10000);
        }

        // Make everything clickable do something random
        document.addEventListener('click', function(e) {
            if (Math.random() > 0.7) {
                e.target.style.transform = `rotate(${Math.random() * 360}deg)`;
            }
        });

        // Konami code activates ultra chaos
        let konamiIndex = 0;
        const konamiCode = ['ArrowUp', 'ArrowUp', 'ArrowDown', 'ArrowDown', 'ArrowLeft', 'ArrowRight', 'ArrowLeft', 'ArrowRight', 'b', 'a'];
        document.addEventListener('keydown', function(e) {
            if (e.key === konamiCode[konamiIndex]) {
                konamiIndex++;
                if (konamiIndex === konamiCode.length) {
                    alert('ULTRA CHAOS MODE ACTIVATED! 🎉');
                    document.body.style.animation = 'rainbow 1s infinite';
                    konamiIndex = 0;
                }
            } else {
                konamiIndex = 0;
            }
        });
    </script>
</body>
</html>
```

## chaos.css

```css
@keyframes float {
    0%, 100% { transform: translateY(0) rotate(0deg); }
    50% { transform: translateY(-50px) rotate(180deg); }
}

@keyframes wobble {
    0%, 100% { transform: translateX(0); }
    25% { transform: translateX(-10px) rotate(-5deg); }
    75% { transform: translateX(10px) rotate(5deg); }
}

@keyframes rainbow {
    0% { filter: hue-rotate(0deg); }
    100% { filter: hue-rotate(360deg); }
}

body {
    font-family: 'Comic Sans MS', cursive;
    overflow-x: hidden;
    transition: background 1s;
}

nav {
    background: linear-gradient(45deg, #ff0000, #00ff00, #0000ff);
    animation: rainbow 3s infinite;
}

nav a {
    color: white;
    text-shadow: 2px 2px 4px rgba(0,0,0,0.8);
}

.project {
    margin: 20px;
    padding: 20px;
    background: rgba(255,255,255,0.8);
    transition: all 0.5s;
}

.project:hover {
    transform: scale(1.1) rotate(5deg);
    box-shadow: 0 10px 50px rgba(0,0,0,0.5);
}
```

---

## Documentation

This portfolio represents a new paradigm in web design: **Chaos-Driven Development**.

Features:
- Quantum superposition of styles
- Non-deterministic navigation
- Messages that go nowhere
- Reality-bending buttons
- Emoji rain
- Self-destructing footer
- Konami code support
- Complete disregard for UX principles

**Warning:** May cause confusion, laughter, or existential crisis.

---
