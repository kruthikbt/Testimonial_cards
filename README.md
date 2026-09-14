from pathlib import Path
import shutil, zipfile

src = Path("/mnt/data/b3db77b4-a523-4f24-aa02-6cc04dfad02d.png")
folder = Path("/mnt/data/testimonial_cards_github_readme")
folder.mkdir(exist_ok=True)
shutil.copy2(src, folder / "testimonial-preview.png")

svg = '''<svg xmlns="http://www.w3.org/2000/svg" width="1200" height="240" viewBox="0 0 1200 240">
<defs>
<linearGradient id="g"><stop stop-color="#07113d"/><stop offset=".5" stop-color="#24105d"/><stop offset="1" stop-color="#50137a"/></linearGradient>
<linearGradient id="t"><stop stop-color="#fff"/><stop offset=".5" stop-color="#4de8ff"/><stop offset="1" stop-color="#d38aff"/></linearGradient>
<filter id="glow"><feGaussianBlur stdDeviation="4" result="b"/><feMerge><feMergeNode in="b"/><feMergeNode in="SourceGraphic"/></feMerge></filter>
</defs>
<rect width="1200" height="240" rx="24" fill="url(#g)"/>
<circle cx="100" cy="70" r="45" fill="#168cff" opacity=".22" filter="url(#glow)">
<animate attributeName="cy" values="70;175;70" dur="5s" repeatCount="indefinite"/>
</circle>
<circle cx="1090" cy="175" r="55" fill="#a855f7" opacity=".2" filter="url(#glow)">
<animate attributeName="cy" values="175;55;175" dur="6s" repeatCount="indefinite"/>
</circle>
<path d="M-30 185 C180 70 320 245 520 125 S880 65 1230 170" fill="none" stroke="#38ddff" stroke-width="3" opacity=".6">
<animate attributeName="d" values="M-30 185 C180 70 320 245 520 125 S880 65 1230 170;M-30 145 C180 245 320 55 520 150 S880 220 1230 105;M-30 185 C180 70 320 245 520 125 S880 65 1230 170" dur="7s" repeatCount="indefinite"/>
</path>
<text x="600" y="92" text-anchor="middle" font-family="Arial" font-size="52" font-weight="700" fill="url(#t)" filter="url(#glow)">TESTIMONIAL CARDS
<animate attributeName="opacity" values=".65;1;.65" dur="3s" repeatCount="indefinite"/></text>
<text x="600" y="132" text-anchor="middle" font-family="Arial" font-size="20" letter-spacing="4" fill="white">RESPONSIVE • ANIMATED • INTERACTIVE</text>
<text x="600" y="172" text-anchor="middle" font-family="Arial" font-size="15" fill="white" opacity=".8">HTML • CSS • FLEXBOX • MEDIA QUERIES • TRANSFORMS</text>
<circle cx="335" cy="202" r="4" fill="#5deaff"><animate attributeName="r" values="3;7;3" dur="1.8s" repeatCount="indefinite"/></circle>
<circle cx="865" cy="40" r="4" fill="#d38aff"><animate attributeName="r" values="3;7;3" dur="2s" repeatCount="indefinite"/></circle>
</svg>'''
(folder / "animated-banner.svg").write_text(svg, encoding="utf-8")

readme = '''<div align="center">

<img src="./animated-banner.svg" width="100%" alt="Animated Testimonial Cards Banner">

# 💬 Testimonial Cards

### Responsive • Animated • Interactive

A modern testimonial section built to present customer feedback and create trust through social proof.

</div>

---

## ✨ About the Project

**Testimonial Cards** are an important component of many websites because they provide **social proof**. Customer experiences help visitors build trust in a product, service, brand, or business and can increase confidence in taking action.

This project focuses on creating a clean testimonial UI that works across desktop and mobile devices.

## 🖼️ Project Preview

<p align="center">
<img src="./testimonial-preview.png" width="90%" alt="Testimonial Cards Project Preview">
</p>

## 🚀 Features

- ⭐ User ratings and testimonials
- 👤 Profile/user sections
- 📱 Responsive mobile layout
- ✨ Hover animations
- 🔄 CSS transform effects
- 🎬 Smooth transitions
- 📐 Flexbox layout
- 🌌 Animated background

## 🧠 Concepts Used

- **Flexbox** — card layout and alignment
- **Media Queries** — responsive mobile design
- **Transitions** — smooth UI changes
- **Transformations** — movement and 3D effects
- **Animations** — interactive visual effects
- **Responsive Design** — adapting the UI to different screen sizes

## 🛠️ Main Challenge

The biggest challenge was making the cards **responsive on mobile phones**.

The original desktop layout did not fit properly on smaller screens. I solved this using **CSS Media Queries**, adjusting the layout and card dimensions according to the screen width.

This project helped me understand that:

> **A good website should not only look good on desktop — it should adapt to the device being used.**

## 📚 What I Learned

- How to build responsive layouts
- How to use Flexbox effectively
- How Media Queries solve mobile layout problems
- How `transition` and `transform` create interactive UI
- How animations can improve user experience
- How to debug responsive CSS issues

## 💻 Tech Stack

**HTML5** • **CSS3**

## 🔗 Links

📂 **Source Code:** `ADD YOUR GITHUB REPOSITORY LINK`

🌐 **Live Demo:** `ADD YOUR DEPLOYED LINK`

---

<div align="center">

### 💙 Built while learning by building.

**More projects coming soon 🚀**

</div>
'''
(folder / "README.md").write_text(readme, encoding="utf-8")

zip_path = Path("/mnt/data/testimonial_cards_github_readme.zip")
with zipfile.ZipFile(zip_path, "w", zipfile.ZIP_DEFLATED) as z:
    for p in folder.iterdir():
        z.write(p, p.name)

print(f"README package created: {zip_path}")
