**Course:** Web Development Fundamentals
**Assignment Type:** Practical / Applied Tasks
**Due Date:** March 22, 2026
**Total Points:** 100

---

## Project: Build a Responsive Portfolio Website

Create a professional portfolio website that showcases your work and demonstrates your web development skills.

---

## Task 1: HTML Structure (25 points)

Create a well-structured HTML5 website with the following pages:

### Required Pages:
1. **Home Page (index.html)** - 8 points
   - Hero section with your name and tagline
   - Brief introduction
   - Navigation menu
   - Footer with contact information

2. **About Page (about.html)** - 6 points
   - Professional bio (150-200 words)
   - Skills section with list of technical skills
   - Education and/or experience timeline

3. **Projects Page (projects.html)** - 6 points
   - At least 3 project cards with:
     - Project title
     - Description
     - Technologies used
     - Link to demo/repository

4. **Contact Page (contact.html)** - 5 points
   - Contact form with fields:
     - Name (required)
     - Email (required)
     - Subject
     - Message (textarea)
     - Submit button

### HTML Requirements:
- Use semantic HTML5 tags (header, nav, main, section, article, footer)
- Proper document structure with DOCTYPE, head, and body
- Include meta tags for character set and viewport
- All forms must have proper labels and input types
- All images must have alt attributes

---

## Task 2: CSS Styling (30 points)

Create an external stylesheet (styles.css) with the following:

### Layout and Design (15 points)
- Consistent color scheme (define at least 3 colors)
- Professional typography (use Google Fonts)
- Proper spacing and margins
- Box model understanding demonstrated
- Flexbox or Grid layout for page sections

### Responsive Design (15 points)
- Website must be fully responsive
- Test on at least 3 breakpoints:
  - Mobile (< 768px)
  - Tablet (768px - 1024px)
  - Desktop (> 1024px)
- Use media queries appropriately
- Navigation menu should collapse on mobile (hamburger menu optional but recommended)
- Images should scale appropriately
- Text should remain readable at all sizes

---

## Task 3: Interactive Features with JavaScript (20 points)

Add JavaScript functionality (script.js):

### Required Features:

1. **Form Validation (8 points)**
   - Validate that name and email fields are not empty
   - Validate email format using regex
   - Display error messages for invalid inputs
   - Show success message on valid submission
   - Prevent form submission if validation fails

2. **Dynamic Content (7 points)**
   - Implement a "dark mode" toggle button
   - Theme preference should persist (use localStorage)
   - Smooth transitions between themes

3. **Interactivity (5 points)**
   - Smooth scrolling for navigation links
   - Add "scroll to top" button that appears when user scrolls down
   - Optional: Image carousel or modal for project screenshots

---

## Task 4: Accessibility and Best Practices (15 points)

### Accessibility (10 points)
- Color contrast meets WCAG 2.1 AA standards
- Keyboard navigation works for all interactive elements
- ARIA labels where appropriate
- Focus indicators visible on all focusable elements
- Proper heading hierarchy (h1, h2, h3)

### Best Practices (5 points)
- Code is well-organized and commented
- CSS follows BEM or similar naming convention
- No inline styles or JavaScript
- External files properly linked
- Cross-browser compatibility (Chrome, Firefox, Safari)

---

## Task 5: Deployment and Documentation (10 points)

### Deployment (5 points)
Deploy your website using ONE of the following:
- GitHub Pages
- Netlify
- Vercel
- Any other free hosting service

Provide the live URL in your submission.

### Documentation (5 points)
Create a README.md file including:
- Project description
- Technologies used
- Features implemented
- How to run locally
- Link to live site
- Screenshots (at least 2)
- Any challenges faced and how you solved them

---

## Bonus Tasks (Optional - Up to +15 points)

Choose ONE or more:
- **Animations (+5 points):** Add CSS animations or transitions
- **Advanced JavaScript (+5 points):** Implement project filtering by technology
- **Performance (+5 points):** Optimize images, achieve >90 Lighthouse score
- **Additional Page (+5 points):** Add a blog page with at least 2 articles

---

## Submission Requirements

### File Structure:
```
portfolio/
├── index.html
├── about.html
├── projects.html
├── contact.html
├── css/
│   └── styles.css
├── js/
│   └── script.js
├── images/
│   └── (all image files)
├── README.md
└── screenshots/
    └── (at least 2 screenshots)
```

### Submission:
1. Compress your project folder into a ZIP file: `StudentID_A5_Portfolio.zip`
2. Include a separate text file with:
   - Your live website URL
   - GitHub repository link (if applicable)
3. Submit via the course portal before the deadline

---

## Grading Rubric

| Task | Points | Key Criteria |
|------|--------|--------------|
| HTML Structure | 25 | Semantic markup, proper structure, all required pages |
| CSS Styling | 30 | Professional design, responsive layout, consistency |
| JavaScript | 20 | Form validation, dark mode, smooth interactions |
| Accessibility | 15 | WCAG compliance, keyboard navigation, best practices |
| Deployment & Docs | 10 | Live site accessible, complete documentation |
| **Total** | **100** | |

---

## Evaluation Criteria

Your website will be tested on:
- Multiple browsers (Chrome, Firefox, Safari)
- Multiple devices (desktop, tablet, mobile)
- Accessibility tools (WAVE, Lighthouse)
- Code quality (W3C validators)

---

## Resources

- HTML Validator: https://validator.w3.org/
- CSS Validator: https://jigsaw.w3.org/css-validator/
- Color Contrast Checker: https://webaim.org/resources/contrastchecker/
- Google Fonts: https://fonts.google.com/
- Font Awesome Icons: https://fontawesome.com/

---

**Note:** Websites that are not responsive or accessible will receive significant point deductions. Test thoroughly before submission!
