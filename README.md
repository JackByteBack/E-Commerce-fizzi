# 🥤 Fizzi — 3D Animated E-Commerce Landing Page

<p align="center">
  <img src="public/hdr/lobby.hdr" alt="Fizzi Banner" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Next.js-14-black?logo=nextdotjs" />
  <img src="https://img.shields.io/badge/React-18-61DAFB?logo=react" />
  <img src="https://img.shields.io/badge/Three.js-0.167-black?logo=threedotjs" />
  <img src="https://img.shields.io/badge/GSAP-3.12-88CE02?logo=greensock" />
  <img src="https://img.shields.io/badge/Tailwind_CSS-v3-38BDF8?logo=tailwindcss" />
  <img src="https://img.shields.io/badge/Prismic-CMS-5163BA?logo=prismic" />
  <img src="https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript" />
</p>

<p align="center">
  A fully animated, 3D e-commerce landing page for the fictional soda brand <strong>Fizzi</strong> — built with Next.js, React Three Fiber, GSAP ScrollTrigger, and Prismic CMS.
</p>

<p align="center">
  <a href="https://github.com/JackByteBack/E-Commerce-fizzi">View Repo</a> •
  <a href="https://dub.sh/fizzi">Course Docs</a>
</p>

---

## ✨ Features

- **3D Soda Can** rendered with React Three Fiber & GLTF model
- **Scroll-driven animations** via GSAP ScrollTrigger
- **Flavor carousel** — switch between 5 soda flavors with animated transitions
- **Animated bubble particles** using Three.js instanced meshes
- **CMS-powered content** through Prismic slices
- **Wavy circle SVG animations** & circular spinning text
- **Text splitting** for per-character entrance animations
- **Responsive design** with Tailwind CSS v3
- **Accessibility** — respects `prefers-reduced-motion`
- **Zustand** for lightweight 3D scene state management

---

## 🛠️ Tech Stack

| Category     | Technology               |
| ------------ | ------------------------ |
| Framework    | Next.js 14 (App Router)  |
| Language     | TypeScript 5             |
| Styling      | Tailwind CSS v3          |
| 3D Rendering | React Three Fiber + Drei |
| 3D Model     | Three.js / GLTF          |
| Animation    | GSAP 3 + ScrollTrigger   |
| CMS          | Prismic                  |
| State        | Zustand                  |
| Fonts        | Alpino (custom)          |

---

## 📁 Project Structure

```
E-Commerce-fizzi/
├── public/
│   ├── Soda-can.gltf          # 3D soda can model
│   ├── Soda-can.bin
│   ├── labels/                # Flavor label textures
│   │   ├── lemon-lime.png
│   │   ├── grape.png
│   │   ├── cherry.png
│   │   ├── strawberry.png
│   │   └── watermelon.png
│   ├── hdr/                   # Environment lighting
│   └── fonts/
│
├── src/
│   ├── app/                   # Next.js App Router pages
│   ├── components/            # Shared UI components
│   │   ├── Bounded.tsx        # Layout wrapper
│   │   ├── Button.tsx
│   │   ├── CircleText.tsx     # Spinning circular SVG text
│   │   ├── FizziLogo.tsx      # Animated SVG logo
│   │   ├── FloatingCan.tsx    # Floating 3D can wrapper
│   │   ├── Footer.tsx
│   │   ├── Header.tsx
│   │   ├── SodaCan.tsx        # Core 3D can component
│   │   ├── TextSplitter.tsx   # Per-character text animation
│   │   └── ViewCanvas.tsx     # R3F canvas setup
│   ├── hooks/
│   │   ├── useMediaQuery.ts   # SSR-safe media query hook
│   │   └── useStore.ts        # Zustand store
│   └── slices/                # Prismic content slices
│       ├── Hero/              # Hero section + Bubbles + TextSplitter
│       ├── AlternatingText/   # Alternating feature text
│       ├── BigText/
│       ├── Carousel/          # Flavor picker carousel
│       └── SkyDive/
│
├── customtypes/               # Prismic custom types
├── tailwind.config.js
├── next.config.mjs
└── slicemachine.config.json
```

---

## 🚀 Getting Started

**1. Run the content setup script:**

```bash
npm run set-up-content
```

**2. Open the migration release in Prismic and publish it** (the URL will be printed in your terminal).

**3. Configure Slice Simulator URL:**

```
http://localhost:3000/slice-simulator
```

**4. Start the dev server:**

```bash
npm run dev
```

This runs Next.js and Slice Machine concurrently.

---

### Option 2 — Clone this Repo Directly

```bash
git clone https://github.com/JackByteBack/E-Commerce-fizzi.git
cd E-Commerce-fizzi
npm install
```

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000)

---

## 🧩 Tools

| Slice             | Description                                                       |
| ----------------- | ----------------------------------------------------------------- |
| `Hero`            | Full-screen hero with 3D can, animated text, and bubble particles |
| `AlternatingText` | Feature sections with alternating left/right layout               |
| `BigText`         | Large display text for section breaks                             |
| `Carousel`        | Interactive flavor picker with animated soda can                  |
| `SkyDive`         | Scroll-triggered sky dive animation sequence                      |

---

## 🎨 Soda Flavors

| Key                  | Color     | Name                |
| -------------------- | --------- | ------------------- |
| `blackCherry`        | `#710523` | Black Cherry        |
| `grape`              | `#572981` | Grape Goodness      |
| `lemonLime`          | `#164405` | Lemon Lime          |
| `strawberryLemonade` | `#690B3D` | Strawberry Lemonade |
| `watermelon`         | `#4B7002` | Watermelon Crush    |

---

## 🎬 Key Animations

- **GSAP ScrollTrigger** — scroll-driven 3D can rotation and section reveals
- **Instanced Bubbles** — Three.js `InstancedMesh` for 300 performant animated bubble particles
- **Per-character text** — `TextSplitter` component splits words into individually animatable `<span>` elements
- **Wavy circles** — Dual counter-rotating SVG rings using GSAP `useGSAP`
- **Circular text** — CSS `animate-spin-slow` on an SVG path
- **Logo wave mask** — Animated fill mask on the Fizzi SVG logo

---

## 📜 Available Scripts

```bash
npm run dev          # Start Next.js + Slice Machine concurrently
npm run next:dev     # Next.js dev server only
npm run build        # Production build
npm run start        # Start production server
npm run lint         # ESLint
npm run format       # Prettier
```

---

## 🔗 Resources & Documentation

### Core Libraries

- [Next.js Docs](https://nextjs.org/docs)
- [Prismic Docs](https://prismic.io/docs)
- [Tailwind CSS v3](https://v3.tailwindcss.com/docs/installation)
- [GSAP Docs](https://gsap.com/docs/v3/)
- [GSAP ScrollTrigger](https://gsap.com/docs/v3/Plugins/ScrollTrigger/)
- [React Three Fiber](https://r3f.docs.pmnd.rs/)
- [Drei (R3F helpers)](https://drei.pmnd.rs/)
- [Zustand](https://zustand.docs.pmnd.rs/)

### Utilities

- [GSAP Ease Visualizer](https://gsap.com/resources/getting-started/Easing)
- [GLTF → R3F Converter](https://gltf.pmnd.rs/)
- [clsx Docs](https://github.com/lukeed/clsx)
- [Alpino Font](https://fonts.google.com/)
- [R3F-Perf](https://github.com/utsuboco/r3f-perf)

### Accessibility

- [usePrefersReducedMotion](https://www.joshwcomeau.com/react/prefers-reduced-motion/)
- [GSAP MatchMedia](https://gsap.com/docs/v3/GSAP/gsap.matchMedia/)

---

## ⚠️ Tailwind Version Note

> This project uses **Tailwind CSS v3**. Tailwind v4 has a fundamentally different configuration API and is **not compatible**. Install v3 explicitly:

```bash
npm install tailwindcss@3
```

See [v3 installation docs](https://v3.tailwindcss.com/docs/installation) if you run into issues.

---

## 🐛 Troubleshooting

- **Content not loading** — Make sure your `.env.local` is set and content migration was published in Prismic
- **3D model not showing** — Check that `Soda-can.gltf` and `Soda-can.bin` are in `/public/`
- **Tailwind styles broken** — Ensure you're using Tailwind v3, not v4
---

> Built as part of a hands-on course project — BCA student @ TCET Mumbai, focused on full-stack development and interactive web experiences.

---
