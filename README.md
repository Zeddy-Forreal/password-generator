<div align="center">

<img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" />
<img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" />
<img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" />

# 🔐 Password Generator

A sleek, dark-themed password generator built with pure HTML, CSS, and JavaScript. Adjust length, toggle character sets, and generate strong passwords instantly — copy to clipboard with one click.

[Features](#-features) · [Getting Started](#-getting-started) · [File Structure](#-file-structure) · [Customization](#-customization)

</div>

---

## ✨ Features

* 🎚️ **Adjustable Length** — Drag the slider from 6 to 100 characters with a live progress fill
* 🔤 **Custom Character Sets** — Toggle uppercase, lowercase, numbers, and symbols independently
* ⚡ **Instant Generation** — Click once to build a randomized password from your selected character pools
* 📋 **One-Click Copy** — Copy the generated password straight to your clipboard
* 🚫 **Input Validation** — Warns you if no character sets are selected before generating
* 🌗 **Magenta-on-Charcoal UI** — Clean dark theme with a punchy magenta accent and glow-on-hover states
* 📱 **Responsive Layout** — Scales down gracefully for small mobile screens

---

## 🚀 Getting Started

**1. Clone the repository**

```bash
git clone https://github.com/Zeddy-Forreal/Password-Generator.git
cd Password-Generator
```

**2. Open in browser**

No build step, no installs. Just open `index.html` directly:

```bash
# macOS
open index.html

# Windows
start index.html

# Linux
xdg-open index.html
```

**3. Generate a password**

Set your desired length with the slider, check the character types you want included, then hit **Generate**. Click the copy icon to grab it instantly.

---

## 📁 File Structure

```
Password-Generator/
├── index.html          Markup and structure
├── style/
│   └── main.css         All styling, theming, and responsive rules
└── script/
    └── main.js           Password generation logic and DOM interactions
```

---

## ⚙️ How It Works

Each checked character-set checkbox feeds its corresponding pool — letters, uppercase letters, numbers, or symbols — into one combined `allowedChars` array:

```javascript
boxes.forEach((box) => {
    if (box.checked === true) {
        if (box.classList.contains("numbers"))   mix_array(numbers);
        if (box.classList.contains("uppercase")) mix_array(cletters);
        if (box.classList.contains("lowercase")) mix_array(sletters);
        if (box.classList.contains("symbols"))   mix_array(symbols);
    }
});
```

The password is then built by picking random characters from that pool for the chosen length:

```javascript
for (let i = 0; i < len; i++) {
    pass += allowedChars[Math.floor(Math.random() * allowedChars.length)];
}
```

If no character set is selected, the app shows an inline error instead of generating an empty password.

---

## 🎨 Customization

All colors and sizes are CSS custom properties at the top of `main.css`. Edit these to retheme the whole app:

```css
:root {
  --main_color:  #c94cb6;   /* Primary accent color       */
  --sec_color:   #ff7fec;   /* Hover / active accent       */
  --text_color:  #b9b9b9;   /* Secondary text              */
  --background:  #181818;   /* Page background             */
  --background2: #242424;   /* Card / panel background     */
  --normal_size: 1.1rem;    /* Base font size               */
  --big_size:    2rem;      /* Large text size              */
  --small_size:  0.8rem;    /* Checkbox label text size     */
}
```

The minimum generated length can be adjusted by changing the clamp value in `main.js`:

```javascript
range.oninput = () => {
    if (range.value < 6) {
        range.value = 6;   // raise or lower the minimum length here
    }
    length.innerHTML = range.value;
    span.style.width = `${range.value}%`;
};
```

---

<div align="center">

Made with 🖤 by [Zeddy-Forreal](https://github.com/Zeddy-Forreal)

</div>
