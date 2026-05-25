# 🥤 Fizzi — 3D E-Commerce Landing Page

A stunning, interactive 3D e-commerce landing page for **Fizzi**, a fictional soda brand. Built as part of the Prismic + Next.js course, this project showcases advanced web animations, 3D rendering, and modern frontend architecture.

> **Live Site:** [View Demo](#) &nbsp;|&nbsp; **Course:** [Prismic YouTube Course](#)

---

## ✨ Features

- **Interactive 3D Soda Cans** — Rendered with Three.js & React Three Fiber, with real-time label swapping per flavor
- **GSAP Animations** — Smooth scroll-triggered animations, text splitters, and hero transitions
- **Flavor Carousel** — Browse 5 soda flavors (Black Cherry, Grape, Lemon Lime, Strawberry Lemonade, Watermelon Crush) with animated wavy circles
- **Bubble Physics** — Instanced mesh bubbles that float upward using `useFrame`
- **CMS-Powered Content** — All text and slices managed via Prismic
- **Accessible** — Respects `prefers-reduced-motion` via GSAP MatchMedia
- **Responsive Design** — Fully mobile-optimized with Tailwind CSS v3

---

## 🧱 Tech Stack

| Technology | Purpose |
|---|---|
| [Next.js 14](https://nextjs.org/docs) | React framework & routing |
| [Prismic](https://prismic.io/docs) | Headless CMS / Slice Machine |
| [Three.js](https://threejs.org/) | 3D rendering engine |
| [React Three Fiber](https://docs.pmnd.rs/react-three-fiber) | React bindings for Three.js |
| [Drei](https://github.com/pmndrs/drei) | R3F helpers (`useGLTF`, `useTexture`, etc.) |
| [GSAP](https://gsap.com/docs/v3/) | Animation library + ScrollTrigger |
| [Tailwind CSS v3](https://v3.tailwindcss.com/docs/installation) | Utility-first CSS styling |
| [Zustand](https://github.com/pmndrs/zustand) | Lightweight state management |
| [clsx](https://github.com/lukeed/clsx) | Conditional className utility |
| [Vercel](https://vercel.com/docs/frameworks/nextjs) | Deployment platform |

---

## 📁 Project Structure

```
fizzi/
├── public/
│   ├── Soda-can.gltf         # 3D soda can model
│   └── labels/               # Flavor label textures
│       ├── lemon-lime.png
│       ├── grape.png
│       ├── cherry.png
│       ├── strawberry.png
│       └── watermelon.png
├── src/
│   ├── app/                  # Next.js App Router
│   ├── components/
│   │   ├── Bounded.tsx       # Layout wrapper component
│   │   ├── FizziLogo.tsx     # Animated SVG logo
│   │   └── SodaCan.tsx       # 3D can component (R3F)
│   ├── hooks/
│   │   └── useMediaQuery.ts  # SSR-safe media query hook
│   └── slices/
│       ├── Hero/
│       │   ├── index.tsx
│       │   ├── TextSplitter.tsx   # Per-character text animation
│       │   └── Bubbles.tsx        # Instanced mesh bubbles
│       ├── Carousel/
│       │   ├── index.tsx
│       │   ├── ArrowIcon.tsx
│       │   └── WavyCircles.tsx    # GSAP rotating SVG rings
│       └── AlternatingText/
│           └── CircleText.tsx     # Spinning "Love your gut" badge
├── tailwind.config.js
└── slicemachine.config.json
```

---

## 🚀 Getting Started

### Prerequisites

- Node.js 18+
- A [Prismic](https://prismic.io) account (free)

### Installation

```bash
# Clone the repository
git clone https://github.com/JackByteBack/E-Commerce-fizzi.git
cd E-Commerce-fizzi

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env.local
# Add your NEXT_PUBLIC_PRISMIC_ENVIRONMENT variable
```

### Development

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### Prismic Setup

1. Create a Prismic repository
2. Run the Slice Machine: `npm run slicemachine`
3. Push your slice models to Prismic
4. Add content via the Prismic editor

---

## 🎨 Customization

### Soda Flavors

Edit the `FLAVORS` array in `slices/Carousel/index.tsx`:

```ts
const FLAVORS = [
  { flavor: "blackCherry",        color: "#710523", name: "Black Cherry" },
  { flavor: "grape",              color: "#572981", name: "Grape Goodness" },
  { flavor: "lemonLime",          color: "#164405", name: "Lemon Lime" },
  { flavor: "strawberryLemonade", color: "#690B3D", name: "Strawberry Lemonade" },
  { flavor: "watermelon",         color: "#4B7002", name: "Watermelon Crush" },
];
```

### Can Labels

Replace the PNG textures in `/public/labels/` — label dimensions and flip settings are managed in `SodaCan.tsx`.

### Brand / Logo

A Figma file is available with all label templates, renders, and brand assets. The Blender source file for the soda can is included in the course assets zip.

### Tailwind Animations

Custom keyframes are defined in `tailwind.config.js`:

```js
keyframes: {
  "slide-left": {
    "0%":   { transform: "translateX(0)" },
    "100%": { transform: "translateX(-100%)" },
  },
},
animation: {
  "slide-left": "slide-left 3s linear infinite",
  "spin-slow":  "spin 6s linear infinite",
},
```

---

## 📦 Key Components

### `SodaCan.tsx`
Renders the GLTF 3D model with dynamically swapped flavor label textures using `useGLTF` and `useTexture` from Drei.

### `TextSplitter.tsx`
Splits text into individual `<span>` elements per character, enabling per-character GSAP animations in the Hero section.

### `Bubbles.tsx`
Uses Three.js `InstancedMesh` for performant rendering of 300+ animated bubble spheres with randomized speeds via `useFrame`.

### `WavyCircles.tsx`
Two SVG wavy rings that counter-rotate using GSAP — inner ring clockwise (16s), outer ring counter-clockwise (22s).

### `Bounded.tsx`
A reusable section wrapper that applies consistent horizontal padding and max-width centering across all slices.

### `useMediaQuery.ts`
An SSR-safe media query hook built with `useSyncExternalStore` — used to conditionally enable/disable animations.

---

## 🌐 Deployment

### Deploy to Vercel

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel
```

Add your `NEXT_PUBLIC_PRISMIC_ENVIRONMENT` environment variable in the Vercel dashboard.

For automatic redeployment when Prismic content changes, set up a [Prismic Webhook](https://prismic.io/docs/webhooks) pointing to your Vercel deploy hook URL.

---

## ♿ Accessibility

- All animations respect the user's `prefers-reduced-motion` OS setting via [GSAP MatchMedia](https://gsap.com/docs/v3/GSAP/gsap.matchMedia())
- SVG logos include `<title>` elements for screen readers
- Semantic HTML structure throughout

---

## ⚠️ Troubleshooting

| Issue | Solution |
|---|---|
| Tailwind v4 compatibility errors | This project uses **Tailwind v3**. Install it from [v3.tailwindcss.com](https://v3.tailwindcss.com/docs/installation) |
| 3D model not loading | Ensure `Soda-can.gltf` and all textures are in the `/public` directory |
| Prismic slices not rendering | Compare with the [final course repo](https://github.com/prismicio-community/course-fizzi-next) |
| Build errors | Open a thread on [Prismic Community Forums](https://community.prismic.io) |

---

## 📚 Documentation & Resources

**Core**
- [Next.js Docs](https://nextjs.org/docs)
- [Prismic Docs](https://prismic.io/docs)

**Styling**
- [Tailwind CSS v3 Docs](https://v3.tailwindcss.com)
- [clsx Docs](https://github.com/lukeed/clsx)

**3D**
- [React Three Fiber Docs](https://docs.pmnd.rs/react-three-fiber)
- [Drei Docs](https://github.com/pmndrs/drei)
- [GLTF → R3F Converter](https://gltf.pmnd.rs/)

**Animation**
- [GSAP Docs](https://gsap.com/docs/v3/)
- [GSAP ScrollTrigger](https://gsap.com/docs/v3/Plugins/ScrollTrigger/)
- [GSAP Ease Visualizer](https://gsap.com/resources/ease-visualizer/)

**State & Fonts**
- [Zustand Docs](https://github.com/pmndrs/zustand)
- [Font: Alpino](https://fonts.google.com/)
- [Adding Fonts to Next.js](https://nextjs.org/docs/pages/building-your-application/optimizing/fonts)

---

## 📄 License

This project is built for educational purposes as part of the Prismic + Next.js course. Feel free to customize it into your own soda brand!

---

<p align="center">Made with 💚 by <a href="https://github.com/JackByteBack">JackByteBack</a></p>
