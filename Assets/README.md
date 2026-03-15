## 🧩 Code Breakdown | شرح أجزاء الكود



In this section, we will break down the code step by step, explaining the function of each part and how it interacts with the rest of the code. The goal is to simplify understanding and allow easy modifications later.


في هذا القسم سنقوم بتفصيل أجزاء الكود خطوة بخطوة، مع شرح وظيفة كل جزء وكيفية تفاعله مع بقية الكود. الهدف هو تبسيط الفهم وتمكينك من التعديل بسهولة لاحقًا.  

View the full code on GitHub: [here](index.html)

### External Libraries
Loads external libraries for confetti animation, image capture, icons, and Arabic fonts.


يقوم هذا الجزء بتحميل مكتبات خارجية تستخدم لإظهار تأثير الكونفيتي، تحويل الصفحة إلى صورة، إضافة الأيقونات، واستخدام الخطوط العربية.

```
<script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css">
<link href="https://fonts.googleapis.com/css2?family=Amiri:wght@400;700&family=Reem+Kufi:wght@400;700&display=swap" rel="stylesheet">
```

---
## CSS Explaination

### Base Styles & Body Setup
Defines the main body styles including font, text alignment, full-screen height, and animated gradient background.

يحدد هذا الجزء أنماط الجسم الرئيسية مثل نوع الخط، محاذاة النص، ارتفاع الشاشة بالكامل، وخلفية متدرجة متحركة.

```css
body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    text-align: center;
    padding: 20px;
    color: white;
    overflow: hidden;
    height: 100vh;
    margin: 0;
    background: linear-gradient(270deg, #068fb1, #51aee0, #018ea0);
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

.hide-btn {
    opacity: 0 !important;
    pointer-events: none !important;
    transform: scale(0.8) !important;
    transition: all 0.5s ease;
    display: none !important;
}
```

### Background Circles
Defines small animated circles in the background that twinkle and float, adding a festive decorative effect.

يحدد هذا الجزء دوائر صغيرة متحركة في الخلفية تتلألأ وتطفو، لإضافة تأثير احتفالي وجمالي.

```css
.color-circle {
    position: absolute;                                 /* Position absolutely for free placement on screen */
    width: 25px; 
    height: 25px;
    border-radius: 50%;                                 /* Makes the circle perfectly round */
    opacity: 0.4;                                       /* Semi-transparent look */
    pointer-events: none;                               /* Circles don't interfere with clicks */
    z-index: 0;                                         /* Behind main content */
    animation: circleTwinkle 3s infinite alternate;     /* Animates opacity and scale back and forth */
}

@keyframes circleTwinkle {
    from { opacity: 0.3; transform: scale(0.8); }       /* Start slightly smaller and fainter */
    to { opacity: 0.6; transform: scale(1.1); }         /* End slightly bigger and brighter */
}
```

### Main Content
Styles the main greeting area, including Arabic and English titles, ensuring proper font, size, alignment, and layering.

ينسق منطقة التهنئة الرئيسية، بما في ذلك العناوين بالعربية والإنجليزية، مع تحديد الخط، الحجم، المحاذاة، والترتيب الطبقي.

```css
#main-content { 
    z-index: 10;           /* Ensures main content is above background circles */
    max-width: 800px;      /* Limits width for large screens */
    width: 90%;            /* Responsive width for smaller screens */
}

.title-ar { 
    font-family: 'Reem Kufi', sans-serif;       /* Arabic-styled font for the main title */
    font-size: 42px;                            /* Large text for visibility */
    direction: rtl;                             /* Right-to-left text for Arabic */
    margin-bottom: 5px;                         /* Space below the title */
    text-shadow: 2px 2px 10px rgba(0,0,0,0.3);  /* Subtle shadow for readability */
}

.title-en { 
    font-size: 19px;            /* Smaller font for English subtitle */
    margin-bottom: 35px;        /* Space below the subtitle */
    opacity: 0.8;               /* Slightly transparent for subtle effect */
    letter-spacing: 1.5px;      /* Extra spacing for styling */
    text-transform: uppercase;  /* Makes English title all caps */
}
```

### Main Button
Styles the main “Get Greeting” button, including font, color, hover effects, and click animation.

ينسق زر “اضغط للحصول على تهنئتك”، بما في ذلك الخط، اللون، تأثيرات hover، وحركة الضغط عند النقر.

```css
button#main-btn {
    padding: 18px 35px;                             /* Button padding for comfortable click area */
    font-size: 18px;                                /* Text size for readability */
    font-family: 'Reem Kufi', sans-serif;           /* Arabic-styled font */
    border: 1px solid rgba(255, 255, 255, 0.4);     /* Semi-transparent border */
    background: rgba(255, 255, 255, 0.15);          /* Semi-transparent background */
    backdrop-filter: blur(5px);                     /* Blurs background behind button */
    color: #ffffff;                                 /* White text color */
    border-radius: 50px;                            /* Rounded pill-shaped button */
    cursor: pointer;                                /* Pointer cursor on hover */
    transition: all 0.4s ease;                      /* Smooth transitions */
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);      /* Subtle shadow for depth */
    outline: none;                                  /* Remove focus outline */
    line-height: 1.6;                               /* Text line height */
}

button#main-btn:hover {
    transform: translateY(-5px);                    /* Lift button on hover */
    background: rgba(255, 255, 255, 0.25);          /* Slightly brighter background */
    border-color: rgba(255, 255, 255, 0.6);         /* Brighter border */
    box-shadow: 0 12px 40px rgba(0, 0, 0, 0.2);     /* Stronger shadow */
}

button#main-btn:active { 
    transform: translateY(-2px) scale(1.02);     /* Press effect when clicking */
}
```

### Envelope
Styles the envelope container and the envelope itself, including size, background, blur effect, borders, shadow, and flap animation.

ينسق حاوية الظرف والظرف نفسه، بما في ذلك الحجم، الخلفية، تأثير التمويه، الحدود، الظل، وحركة الغطاء العلوي.

```css
#envelope-wrapper {
    margin-top: 40px;                 /* Space above the envelope */
    display: none;                    /* Hidden initially */
    flex-direction: column;           /* Arrange children vertically */
    align-items: center;              /* Center horizontally */
    justify-content: center;          /* Center vertically */
    width: 100%;                      /* Full width */
    perspective: 1000px;              /* Perspective for 3D flip effect */
}

.envelope {
    width: 100%; height: 300px; 
    background: rgba(255, 255, 255, 0.1);       /* Semi-transparent background */
    backdrop-filter: blur(15px);                /* Heavy blur effect */
    border-radius: 20px 20px 10px 10px;         /* Rounded corners, top more rounded */
    border: 2px solid rgba(255, 255, 255, 0.2); /* Light border */
    position: relative;                         /* For positioning the flap */
    box-shadow: 0 15px 35px rgba(0,0,0,0.4);    /* Depth shadow */
    display: flex; 
    align-items: center; 
    justify-content: center; 
    overflow: hidden; 
    transform-origin: center;              /* Pivot point for flip */
}

.envelope::before {
    content: ''; 
    position: absolute; 
    top: 0; 
    left: 0; 
    width: 100%; 
    height: 100%;
    background: rgba(255, 255, 255, 0.15);      /* Semi-transparent flap */
    clip-path: polygon(0 0, 50% 50%, 100% 0);   /* Triangle shape flap */
    transform-origin: top center;               /* Pivot for flip animation */
    transition: transform 0.8s ease-in-out;     /* Smooth flap opening */
    border-bottom: none;
}
```

### Envelope Animations
Defines animations for the envelope: rising from the bottom, flipping the flap, and revealing the greeting text.

يحدد الحركات للظرف: الصعود من الأسفل، قلب الغطاء العلوي، وكشف نص التهنئة.

```css
.show-envelope { 
    display: flex !important;                       /* Show the envelope */
    animation: riseAndOpen 1.8s ease-out forwards;  /* Animate rising and opening */
}

.open-flap::before { 
    transform: rotateX(-180deg);         /* Flip the flap upwards */
    z-index: -1;                         /* Send behind envelope body */
} 

.reveal-greeting { 
    transform: translateY(0%) scale(1) !important;  /* Move greeting into view and scale */
    opacity: 1 !important;                          /* Fully visible */
    bottom: 60px !important;                        /* Position from bottom */
}

@keyframes riseAndOpen {
    0% { transform: translateY(100vh) scale(0.5); opacity: 0; } /* Start below screen, small, invisible */
    40% { transform: translateY(0) scale(1); opacity: 1; }      /* Reach center, normal size, visible */
    60% { transform: translateY(0) scale(1); }                  /* Hold position */
    100% { transform: translateY(-5px) scale(1.02); }           /* Slight bounce at top */
}
```

### Capture Area
Defines the hidden area used to capture the greeting as an image for sharing. It’s positioned off-screen and styled for proper rendering.

يحدد المنطقة المخفية المستخدمة لالتقاط التهنئة كصورة للمشاركة. موضوعة خارج الشاشة ومصممة للعرض بشكل صحيح.

```css
#capture-area {
    position: absolute; 
    left: -9999px; 
    top: -9999px;                     /* Move off-screen to hide */
    width: 600px; 
    height: 500px; 
    display: flex; 
    flex-direction: column; 
    align-items: center; 
    justify-content: center; 
    padding: 40px; 
    box-sizing: border-box;           /* Include padding in width/height */
}

#greeting-capture-copy .ar {
    font-size: 22px !important; 
    margin-bottom: 10px !important;   /* Arabic greeting text styling */
}

#greeting-capture-copy .en {
    font-size: 15px !important;       /* English greeting text styling */
}
```
### Greeting Container
Defines the container inside the envelope that will display the greeting text. Initially hidden and slightly scaled for animation effect.

يحدد الحاوية داخل الظرف التي ستعرض نص التهنئة. مخفية في البداية ومصغرة قليلًا لتأثير الحركة.

```css
#greeting-container {
    position: absolute; 
    top: 5px; 
    left: 0; 
    width: 100%; 
    height: 100%; 
    display: flex; 
    flex-direction: column; 
    justify-content: center; 
    align-items: center;    
    padding: 20px; 
    box-sizing: border-box; 
    transform: translateY(0) scale(0.9);    /* Slightly smaller for animation */
    opacity: 0;                             /* Hidden initially */
    transition: all 0.8s ease-out;          /* Smooth reveal transition */
    z-index: 2;                             /* Above envelope background */
}
```
### Share Button
Styles the "share greeting" button, including hover effects and a pulsing animation. Initially invisible until the greeting appears.

ينسق زر "مشاركة التهنئة"، بما في ذلك تأثير hover وحركة النبض. مخفي في البداية حتى تظهر التهنئة.

```css
.share-btn {
    margin-top: 20px; 
    padding: 10px 25px; 
    font-size: 14px;
    background: rgba(255, 255, 255, 0.2);       /* Semi-transparent background */
    color: white; 
    border: 1px solid rgba(255, 255, 255, 0.4); 
    border-radius: 12px; 
    cursor: pointer; 
    transition: 0.3s; 
    opacity: 0;                                 /* Hidden initially */
    animation: pulseBtn 2s infinite;            /* Pulsing animation */
}

.share-btn:hover {
    background: rgba(255, 255, 255, 0.35); 
    border-color: white; 
    transform: scale(1.05);                     /* Slight enlarge on hover */
}

@keyframes pulseBtn { 
    0% { box-shadow: 0 0 0 0 rgba(255,255,255,0.3); } 
    70% { box-shadow: 0 0 0 10px rgba(255,255,255,0); } 
    100% { box-shadow: 0 0 0 0 rgba(255,255,255,0); } 
}
```

### Greeting Text
Styles the greeting text in both Arabic and English. Arabic text uses a serif font with right-to-left direction, while English uses a smaller, slightly transparent style.

ينسق نص التهنئة باللغتين العربية والإنجليزية. النص العربي يستخدم خط Serif مع اتجاه من اليمين لليسار، بينما الإنجليزية أصغر مع شفافية طفيفة.

```css
.ar { 
    font-family: 'Amiri', serif;         /* Arabic serif font */
    font-size: 28px;                     /* Larger font for Arabic */
    direction: rtl;                      /* Right-to-left text */
    margin-bottom: 15px; 
    line-height: 1.5; 
    color: white; 
    text-shadow: 1px 1px 3px rgba(0,0,0,0.5);   /* Subtle shadow */
}

.en { 
    font-size: 19px;                     /* Smaller font for English */
    line-height: 1.4; 
    opacity: 0.9;                        /* Slight transparency */
    color: #f0e6ff; 
}
```

### Footer and Social Links
Styles the footer credit and social media links. Footer stays fixed at the bottom, while social icons have hover effects to slightly lift and highlight them.

ينسق الفوتر وروابط وسائل التواصل الاجتماعي. يبقى الفوتر مثبتًا أسفل الصفحة، وأيقونات التواصل تتحرك قليلًا عند المرور عليها لتسليط الضوء عليها.

```css
.footer-credit {
    position: fixed;                /* Keep footer at bottom */
    bottom: 15px;
    left: 0;
    width: 100%;
    font-size: 15px;
    color: rgba(255, 255, 255, 0.7); /* Semi-transparent text */
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
    color: rgb(255, 255, 255); 
    transform: translateY(-3px);     /* Slight lift on hover */
}
```

### Mobile Adjustments
Applies responsive design for screens smaller than 600px. Adjusts font sizes, button sizes, envelope dimensions, and footer layout to fit smaller devices.

تطبيق تصميم متجاوب للشاشات الأصغر من 600 بكسل. يضبط أحجام الخطوط، وأحجام الأزرار، وأبعاد الظرف، وتنسيق الفوتر لتناسب الأجهزة الصغيرة.

```css
@media (max-width: 600px) {

    body { padding: 10px; justify-content: flex-start; padding-top: 15vh; }

    .title-ar { font-size: 32px; } 
    .title-en { font-size: 15px; margin-bottom: 20px; }

    button#main-btn { width: 85%; font-size: 17px; padding: 15px; }

    .copy-btn { margin-top: 12px; padding: 6px 15px; font-size: 11px; border-radius: 8px; }

    #envelope-wrapper { margin-top: 20px; width: 95%; }     
    .envelope { height: 250px; }

    .ar { font-size: 19px; line-height: 1.4; }
    .en { font-size: 13px; }

    .footer-credit { font-size: 11px; bottom: 10px; background: rgba(0,0,0,0.1); padding: 5px 0; }
    .social-links a { font-size: 22px; margin: 0 10px; }
}
```

---
## HTML Explaination

### Body & Audio
Defines the main `<body>` of the HTML and includes an audio element for the button click sound. The `preload="auto"` ensures the sound loads when the page opens.

تعريف جسم الصفحة الرئيسي `<body>` وإضافة عنصر صوت لتشغيل صوت الضغط على الزر. الخاصية `preload="auto"` تضمن تحميل الصوت عند فتح الصفحة.

```html
<body>

<audio id="clickSound" src="ButtonClickSound.mp3" preload="auto"></audio>
```

### Main Content
This section contains the main visible content: the Arabic and English titles, and the main button.  
Clicking the button triggers the `startGreetingSequence()` function to show the greeting.

هذا القسم يحتوي على المحتوى الرئيسي الظاهر: العنوان بالعربية والإنجليزية، وزر التشغيل الرئيسي.  
عند الضغط على الزر، يتم استدعاء الدالة `startGreetingSequence()` لإظهار التهنئة.

```html
<div id="main-content">
    <div class="title-ar">لنشارك فرحة العيد معاً</div>
    <div class="title-en">Let’s share the joy of Eid together</div>

    <button id="main-btn" onclick="startGreetingSequence()">
        اضغط للحصول على تهنئتك <br>
        Click for your greeting
    </button>
</div>
```

### Envelope Section
This section contains the envelope wrapper that holds the greeting card and the share button.  
- The envelope initially is hidden and animates open when the greeting sequence starts.  
- The `greeting-container` will display the randomly selected Eid greeting.  
- The `share-btn` allows users to share or download their greeting image via the `shareGreeting()` function.

هذا القسم يحتوي على غلاف الظرف الذي يحتوي على بطاقة التهنئة وزر المشاركة.  
- الظرف يكون مخفيًا في البداية ويفتح مع بدء تسلسل التهنئة.  
- `greeting-container` سيعرض التهنئة العشوائية لعيد الفطر.  
- زر `share-btn` يسمح للمستخدم بمشاركة أو تحميل صورة التهنئة من خلال الدالة `shareGreeting()`.

```html
<div id="envelope-wrapper">
    <div class="envelope" id="envelope-body">
        <div id="greeting-container">
            <div id="greeting"></div>
        </div>
    </div>
    <button class="share-btn" id="share-btn" onclick="shareGreeting()">
         share the greeting! | !شارك التهنئه
    </button>
</div>
```

### Capture Area
This hidden area is used to generate the shareable image of the greeting.  
- `temp-circles` temporarily clones the background circles for the captured image.  
- Arabic and English titles are repeated here for the captured version.  
- `greeting-capture-copy` contains the greeting text that will be captured.  
- Developer credit is included at the bottom.  

هذه المنطقة المخفية تستخدم لإنشاء صورة قابلة للمشاركة للتهنئة.  
- `temp-circles` ينسخ مؤقتًا دوائر الخلفية للصورة الملتقطة.  
- العناوين العربية والإنجليزية مكررة هنا للإصدار الذي سيتم التقاطه.  
- `greeting-capture-copy` يحتوي على نص التهنئة الذي سيتم التقاطه.  
- تم تضمين حقوق المطور في الأسفل.

```html
<div id="capture-area">
    <div id="temp-circles"></div>
    <div class="title-ar" style="font-size:36px;">لنشارك فرحة العيد معاً</div>
    <div class="title-en" style="font-size:16px;">Let’s share the joy of Eid together</div>
    <div class="envelope" style="width:100%; height:280px; overflow:visible; border-radius:20px;">
        <div id="greeting-capture-copy" style="text-align:center; padding:20px; display:flex; flex-direction:column; justify-content:center; height:100%;"></div>
    </div>
    <div style="font-size:12px; margin-top:10px; opacity:0.6; color:white;"> تم التطوير بواسطة ديالى التركي</div>
    <div style="font-size:12px; margin-top:10px; opacity:0.6; color:white;"> Developed by Diyala Alturki</div>
</div>
```

### Footer
Contains developer credits and social media links.  
- Shows the developer name in Arabic and English.  
- Links to LinkedIn, GitHub, and email for contact.  

يحتوي على حقوق المطور وروابط التواصل الاجتماعي.  
- يعرض اسم المطور بالعربية والإنجليزية.  
- روابط إلى LinkedIn وGitHub والبريد الإلكتروني للتواصل.

```html
<footer class="footer-credit" id="footer-to-hide">
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

---
## JavaScript Explaination

### Greetings Data
Holds an array of greeting messages in Arabic and English.  
- Each object has `ar` for Arabic text and `en` for English text.  
- Used later to display a random Eid greeting when the user clicks the button.  

يحوي مصفوفة من رسائل التهاني بالعربية والإنجليزية.  
- كل عنصر يحتوي على `ar` للنص العربي و `en` للنص الإنجليزي.  
- تستخدم لاحقًا لعرض تهنئة عشوائية عند ضغط المستخدم على الزر.

```javascript
const greetings = [
    { ar:"أدام الله عليكم الأعياد دهورًا، وألبسكم من تقواه نورًا، عيدكم مبارك.", en:"May Allah grant you many years of Eids and clothe you with the light of His piety. Blessed Eid to you."},
    ...
];
```

### Start Greeting Sequence
This function runs when the user clicks the main button.  
- Plays a click sound.  
- Hides the main button.  
- Launches confetti animation.  
- Shows the envelope and animates it opening.  
- Picks a random greeting from `greetings` and displays it.  
- Reveals the share button.  


يتم تنفيذ هذه الدالة عند ضغط المستخدم على الزر الرئيسي.  
- تشغيل صوت النقر.  
- إخفاء الزر الرئيسي.  
- إطلاق تأثير الكونفيتي.  
- إظهار الظرف وتحريك فتحه.  
- اختيار تهنئة عشوائية من مصفوفة `greetings` وعرضها.  
- إظهار زر المشاركة.

```javascript
function startGreetingSequence() {

    const audio = document.getElementById('clickSound');
    audio.play(); // play button click sound

    const btn = document.getElementById("main-btn");
    const shareBtn = document.getElementById("share-btn");
    btn.classList.add("hide-btn"); // hide main button

    // launch confetti
    confetti({ particleCount: 150, spread: 80, origin: { y: 0.6 }, colors: ['#ffffff', '#ffd700', '#7b3fe4'] });

    const wrapper = document.getElementById("envelope-wrapper"),
        body = document.getElementById("envelope-body"),
        container = document.getElementById("greeting-container"),
        display = document.getElementById("greeting");

    wrapper.style.display = "flex";
    wrapper.classList.add("show-envelope"); // show envelope

    setTimeout(() => body.classList.add("open-flap"), 1200); // animate flap opening
    setTimeout(() => {
        const randomIndex = Math.floor(Math.random() * greetings.length); // pick random greeting
        display.innerHTML = `<div class='ar'>${greetings[randomIndex].ar}</div><div class='en'>${greetings[randomIndex].en}</div>`;
        container.classList.add("reveal-greeting"); // reveal greeting text
        shareBtn.style.opacity = "1"; // show share button
    }, 1800);
}
```

### Share Greeting
This function allows the user to share their Eid greeting as an image.  
- Copies the greeting content into a hidden capture area.  
- Clones background circles for visual consistency.  
- Uses `html2canvas` to render the capture area into a canvas.  
- Converts the canvas to an image file.  
- If supported, uses the Web Share API to share the image.  
- Otherwise, triggers a download of the image.  


تسمح هذه الدالة للمستخدم بمشاركة تهنئته كصورة.  
- نسخ محتوى التهنئة إلى منطقة مخفية للالتقاط.  
- نسخ الدوائر الخلفية للحفاظ على الشكل البصري.  
- استخدام `html2canvas` لتحويل المنطقة إلى صورة.  
- تحويل الصورة إلى ملف.  
- إذا كانت متاحة، استخدام Web Share API لمشاركة الصورة.  
- وإلا، تنزيل الصورة مباشرة.

```javascript
async function shareGreeting() {
    const captureArea = document.getElementById("capture-area");
    const tempCirclesContainer = document.getElementById("temp-circles");

    // copy current greeting to hidden capture area
    document.getElementById("greeting-capture-copy").innerHTML =
        document.getElementById("greeting").innerHTML;

    // clone background circles for the capture
    const originalCircles = document.querySelectorAll('.color-circle');
    tempCirclesContainer.innerHTML = '';
    originalCircles.forEach(circle => {
        const clone = circle.cloneNode(true);
        clone.style.animation = 'none'; 
        tempCirclesContainer.appendChild(clone);
    });

    try {
        // render the capture area to canvas
        const canvas = await html2canvas(captureArea, {
            backgroundColor: null, scale: 3, useCORS: true,
            onclone: (clonedDoc) => {
                const el = clonedDoc.getElementById('capture-area');
                el.style.background = getComputedStyle(document.body).background;
                el.style.display = 'flex';
            }
        });

        // convert canvas to image file
        const dataUrl = canvas.toDataURL("image/png");
        const blob = await (await fetch(dataUrl)).blob();
        const file = new File([blob], "Eid_Greeting.png", { type: "image/png" });

        if (navigator.share) {
            // use Web Share API if supported
            await navigator.share({ files: [file], title: 'تهنئة عيد', text: 'عيدكم مبارك' });
        } else {
            // fallback: download the image
            const link = document.createElement('a');
            link.download = 'Eid_Greeting.png';
            link.href = dataUrl;
            link.click();
        }
    } catch (err) { console.error(err); }
}
```

### Background Circle Generator
This section dynamically generates colorful floating circles for the background animation.  
- Defines a color palette for the circles.  
- Creates 80 circles with random positions and colors.  
- Sets a random animation delay for each circle to create a twinkling effect.  
- Appends the circles to the document body.  

مولد الدوائر الخلفية
يقوم هذا الجزء بإنشاء دوائر ملونة متحركة للخلفية.  
- تحديد لوحة ألوان للدوائر.  
- إنشاء 80 دائرة بأماكن وألوان عشوائية.  
- تعيين تأخير عشوائي لكل دائرة لإعطاء تأثير الوميض.  
- إضافة الدوائر إلى جسم الصفحة.

```javascript
const colors = ['#ff74c1', '#fdfdfd', '#ffeaa7', '#a29bfe', '#55efc4', '#fffa65'];

for (let i = 0; i < 80; i++) {
    let circle = document.createElement("div");
    circle.className = "color-circle";
    circle.style.top = Math.random() * 100 + "vh";                                  // random vertical position
    circle.style.left = Math.random() * 100 + "vw";                                 // random horizontal position
    circle.style.background = colors[Math.floor(Math.random() * colors.length)];    // random color
    circle.style.animationDelay = Math.random() * 5 + "s";                          // random animation start time

    document.body.appendChild(circle);                                              // add circle to page
}
```
