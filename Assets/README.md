# Eid Greeting Generator 🎉

A simple web project that generates random Eid greetings in Arabic and English.

View the full code on GitHub: [here](index.html)

## Features

- Random Arabic & English greetings
- Copy-to-clipboard button
- Confetti animation
- Floating twinkling stars
- Fully responsive for mobile & desktop
- Social media links in footer (LinkedIn, GitHub, Email)

## How it works

### 1. HTML Structure (`index.html`)

### 1.1 Main Content

```html
<div id="main-content">
    <div class="title-ar">لنشارك فرحة العيد معاً</div>
    <div class="title-en">Let’s share the joy of Eid together</div>

    <button id="main-btn" onclick="generateGreeting()">
        اضغط للحصول على تهنئة عشوائية <br>
        Click for a random greeting
    </button>

    <div id="greeting-container">
        <div id="greeting"></div>
        <button class="copy-btn" id="copy-btn" onclick="copyGreeting()">
            نسخ التهنئة | Copy Text
        </button>
    </div>
</div>
```

**Explanation:**
- `.title-ar` : Shows Arabic title
- `.title-en` : Shows English title
- `#main-btn` : Button that triggers a random greeting
- `#greeting-container` :Hidden at first, appears when you click the button
- `.copy-btn` : Copies the greeting to clipboard

#### 1.2 Footer

```html
<footer class="footer-credit">
    <div>Developed by Diyala Alturki | تم التطوير بواسطة ديالى التركي</div>
    <div class="social-links">
        <a href="https://www.linkedin.com/in/diyala-alturki" target="_blank">
            <i class="fab fa-linkedin"></i>
        </a>
        <a href="https://github.com/Diiiyala" target="_blank">
            <i class="fab fa-github"></i>
        </a>
        <a href="mailto:diyala.alturki@gmail.com">
            <i class="fas fa-envelope"></i>
        </a>
    </div>
</footer>
```

**Explanation:**
- `.footer-credit` : Displays developer info.
- `.social-links` : Contains clickable icons for LinkedIn, GitHub, and Email.
- Hovering over icons changes their color and slightly moves them up for a subtle effect.

### 2. CSS Styling

#### 2.1 Background Gradient Animation

```
body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    text-align: center;
    padding: 20px;
    color: white;
    overflow: hidden;
    height: 100vh;
    margin: 0;
    background: linear-gradient(270deg, #5e2b97, #7b3fe4, #4a1f7a);
    background-size: 600% 600%;
    animation: gradientMove 15s ease infinite;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

@keyframes gradientMove {
    0% { background-position: 0% 50% }
    50% { background-position: 100% 50% }
    100% { background-position: 0% 50% }
}
```

**Explanation:**
- Full-page gradient with animation
- Flexbox centers the content vertically and horizontally
- Sets default font and white text color

#### 2.2 Star Animations

```
@keyframes starFloat {
    0% { transform: translateY(0) scale(1); }
    100% { transform: translateY(-30px) scale(1.1); }
}

@keyframes twinkle {
    from { opacity: 0.3; }
    to { opacity: 1; }
}

.star {
    position: absolute;
    color: gold;
    pointer-events: none;
    z-index: 0;
    animation: twinkle 2s infinite alternate, starFloat 5s infinite alternate ease-in-out;
}
```

**Explanation:**
- Stars move slightly up and down
- Stars fade in and out to twinkle
- Makes the page feel festive and lively
- `z-index: 0` ensures stars stay behind main content

#### 2.3 Button Styling

```
button#main-btn {
    padding: 18px 35px;
    font-size: 18px;
    font-weight: bold;
    border: none;
    background: white;
    color: #4a1f7a;
    border-radius: 50px;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 10px 20px rgba(0,0,0,0.2);
    outline: none;
}

button#main-btn:hover {
    transform: translateY(-5px) scale(1.05);
    box-shadow: 0 15px 25px rgba(0,0,0,0.3);
    background: #fdfdfd;
}
```

**Explanation:**
- Button has rounded shape and shadow
- Hover effect makes it lift and grow slightly

#### 2.4 Greeting Container Styling

```
#greeting-container {
    background: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(10px);
    border-radius: 25px;
    padding: 30px;
    margin-top: 40px;
    display: none;
    border: 1px solid rgba(255,255,255,0.2);
    animation: fadeIn 0.8s ease;
}

@keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
}

.ar { direction: rtl; font-size: 26px; margin-bottom: 20px; line-height: 1.6; }
.en { font-size: 19px; line-height: 1.4; opacity: 0.9; font-style: italic; }
```

**Explanation:**
- Hidden by default, fades in with blur effect
- `.ar` and `.en` styles define Arabic/English text formatting

#### 2.5 Copy Button Styling

```
.copy-btn {
    margin-top: 20px;
    padding: 10px 25px;
    font-size: 14px;
    background: rgba(255, 255, 255, 0.2);
    color: white;
    border: 1px solid rgba(255, 255, 255, 0.4);
    border-radius: 12px;
    cursor: pointer;
    transition: 0.3s;
    outline: none;
}

.copy-btn:hover {
    background: rgba(255, 255, 255, 0.35);
    border-color: white;
}
```

**Explanation:**
- Styled smaller button for copying greeting
- Hover effect brightens background and border

#### 2.6 Footer & Social Links

```
.footer-credit {
    position: fixed;
    bottom: 15px;
    left: 0;
    width: 100%;
    font-size: 13px;
    color: rgba(255, 255, 255, 0.7);
    z-index: 20;
}

.social-links {
    margin-top: 10px;
}

.social-links a {
    color: white;
    margin: 0 12px;
    text-decoration: none;
    opacity: 0.7;
    transition: all 0.3s ease;
    font-size: 25px;
    display: inline-block;
}

.social-links a:hover {
    opacity: 1;
    color: gold;
    transform: translateY(-3px);
}
```

**Explanation:**
- Footer fixed at bottom with subtle transparency
- Social icons highlight and lift on hover

#### 2.7 Responsive Design

```
@media (max-width: 600px) {
    body { padding: 10px; }
    .title-ar { font-size: 34px; } 
    .title-en { font-size: 16px; }
    button#main-btn { width: 90%; font-size: 18px; padding: 18px; }
    #greeting-container { width: 90%; margin: 30px auto; padding: 30px 20px; }
    .ar { font-size: 24px; }
    .en { font-size: 16px; }
    .footer-credit { font-size: 11px; bottom: 15px; }
    .social-links a { font-size: 24px; margin: 0 12px; }
}
```
**Explanation:**
- Makes the page mobile-friendly
- Adjusts font sizes, button width, and spacing for smaller screens

### 3. JavaScript Logic

#### 3.1 Greetings Array

```javascript
const greetings = [
  { ar: "أدام الله عليكم الأعياد دهورًا ...", en: "May Allah grant you many years of Eids ..." },
  { ar: "كل عام وأنتم بألف خير ...", en: "Wishing you goodness every year ..." },
  // more greetings
];
```

**Explanation:**
- Stores Arabic and English greetings
- One is picked randomly each time


#### 3.2 Generate Greeting Function

```javascript
function generateGreeting() {
  // Confetti animation
  confetti({ particleCount: 150, spread: 70, origin: { y: 0.6 }, colors: ['#ffffff', '#ffd700', '#7b3fe4'] });

  // Pick random greeting, avoid last one
  let randomIndex;
  do { randomIndex = Math.floor(Math.random() * greetings.length); }
  while (randomIndex === lastIndex);
  lastIndex = randomIndex;

  // Show greeting
  const container = document.getElementById("greeting-container");
  const display = document.getElementById("greeting");
  container.style.display = "block";
  display.style.opacity = 0;

  setTimeout(() => {
    display.innerHTML = `<div class='ar'>${greetings[randomIndex].ar}</div>
                         <div class='en'>${greetings[randomIndex].en}</div>`;
    display.style.opacity = 1;
    display.style.transition = "opacity 0.3s";
  }, 100);
}
```
**Explanation:**
- Shows confetti
- Picks a random greeting (never repeats last one)
- Displays greeting with a fade-in effect

#### 3.3 Copy to Clipboard

```javascript
function copyGreeting() {
  const greetingDiv = document.getElementById("greeting");
  const text = greetingDiv.innerText;

  navigator.clipboard.writeText(text).then(() => {
    const btn = document.getElementById("copy-btn");
    const originalText = btn.innerText;
    btn.innerText = "تم النسخ! | Copied! ✅";
    btn.style.borderColor = "#ffd700";

    setTimeout(() => {
      btn.innerText = originalText;
      btn.style.borderColor = "rgba(255, 255, 255, 0.4)";
    }, 2000);
  }).catch(err => console.error('Failed to copy:', err));
}
```

**Explanation:**
- Copies the greeting text to the clipboard
- Shows temporary feedback “Copied!”

#### 3.4 Stars Creation Loop

```javascript
for (let i = 0; i < 80; i++) {
  let star = document.createElement("div");
  star.className = "star";
  star.innerHTML = "★";
  star.style.top = Math.random() * 100 + "vh";
  star.style.left = Math.random() * 100 + "vw";
  star.style.animationDelay = Math.random() * 5 + "s";
  star.style.fontSize = (Math.random() * 10 + 10) + "px";
  document.body.appendChild(star);
}
```

**Explanation:**
- Adds 80 stars randomly
- Each star has different position, size, and twinkle delay

---
