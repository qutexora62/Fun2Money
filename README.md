# Fun2Money — Stylish Animated Texts & Fonts

यह रिपॉज़िटरी HTML-आधारित प्रोजेक्ट है जो खूबसूरत और स्टाइलिश एनिमेटेड टेक्स्ट, एनिमेटेड फॉन्ट और टेक्स्ट-एनीमेशन डेमो दिखाता है। README में छोटे-छोटे कोड उदाहरण, उपयोग करने का तरीका और लाइव प्रीव्यू के निर्देश दिए गए हैं ताकि आप जल्द ही अपने पेज पर एनिमेशन लगा सकें।

## Features

- Gradient animated text
- Neon glow text
- Typing / marquee style animated text
- Animated font-size / weight transitions
- Easy Google Fonts integration
- छोटा और पढ़ने योग्य HTML/CSS उदाहरण

## जल्दी शुरू करें (Quick Start)

1. रिपॉज़िटरी क्लोन करें या फाइलें डाउनलोड करें:

```bash
git clone https://github.com/qutexora62/Fun2Money.git
cd Fun2Money
```

2. लोकल प्रीव्यू:
- बस `index.html` को ब्राउज़र में खोलें या VSCode में Live Server इस्तेमाल करें।

3. GitHub Pages पर होस्ट करने के लिए:
- रिपॉज़िटरी सेटिंग्स → Pages → Branch: main (या default branch) → Save

## उदाहरण (Examples)

1) Gradient animated text

```html
<!-- Gradient animated text -->
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap" rel="stylesheet">
<style>
  .gradient-text{
    font-family: 'Poppins', sans-serif;
    font-size: 4rem;
    font-weight: 700;
    background: linear-gradient(90deg, #ff6a00, #ee0979, #8e2de2);
    background-size: 200% 200%;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    animation: gradientShift 4s linear infinite;
  }

  @keyframes gradientShift{
    0%{background-position:0% 50%;}
    50%{background-position:100% 50%;}
    100%{background-position:0% 50%;}
  }
</style>
<h1 class="gradient-text">Fun2Money — Stylish Text</h1>
```

2) Neon glow text

```html
<style>
  .neon{
    font-family: 'Poppins', sans-serif;
    color: #fff;
    font-size: 3rem;
    text-shadow:
      0 0 6px rgba(255,255,255,0.9),
      0 0 12px rgba(255,105,180,0.6),
      0 0 18px rgba(128,0,255,0.5);
    animation: pulse 2s ease-in-out infinite;
  }

  @keyframes pulse{
    0%{text-shadow:0 0 6px rgba(255,255,255,0.9);}
    50%{text-shadow:0 0 20px rgba(255,105,180,0.9);}
    100%{text-shadow:0 0 6px rgba(255,255,255,0.9);}
  }
</style>
<h2 class="neon">Neon Glow</h2>
```

3) Typing animation

```html
<style>
  .typing{
    font-family: monospace;
    font-size: 1.6rem;
    white-space: nowrap;
    overflow: hidden;
    border-right: .12em solid rgba(255,255,255,0.75);
    width: 22ch; /* adjust to text length */
    animation: typing 3s steps(22), blink .7s step-end infinite;
  }

  @keyframes typing{
    from {width: 0}
    to {width: 22ch}
  }
  @keyframes blink{
    50% {border-color: transparent}
  }
</style>
<div class="typing">Design. Animate. Impress.</div>
```

## Fonts & Performance सुझाव
- Google Fonts का `display=swap` उपयोग करें ताकि फॉण्ट लोडिंग ब्लॉक न करे।
- बड़े एनिमेशन के लिए will-change और transform का प्रयोग करें ताकि रेंडरिंग स्मूद रहे।

## Customize करने के टिप्स
- रंग बदलने के लिए gradient के रंग अदला-बदली करें।
- font-size, letter-spacing और animation-duration tweak करें।
- SVG या Canvas जोड़ें अगर आप जटिल टेक्स्ट-मैस्किंग बनाना चाहते हैं।

## Example structure (suggested)

- index.html — डेमो पेज
- assets/css/styles.css — स्टाइल्स
- assets/fonts/ — लोकल फॉन्ट्स (यदि उपयोग करते हैं)

## Contribution
यदि आप नया एनिमेशन जोड़ना चाहते हैं तो Pull Request भेजें — छोटे HTML + CSS example के साथ।

## License
MIT

---

Enjoy! ✨
