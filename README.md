# DistroFinder

![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Vitest](https://img.shields.io/badge/Vitest-6E9F18?style=flat-square&logo=vitest&logoColor=white)
![ESLint](https://img.shields.io/badge/ESLint-4B32C3?style=flat-square&logo=eslint&logoColor=white)

## 📚 Overview

DistroFinder is a frontend-first **Next.js** application for exploring Linux distributions, comparing them side by side, and getting personalized recommendations.

This repository was migrated from a React + React Router app to the **Next.js App Router**, with routes now defined under `src/app` and navigation handled through `next/link` and `next/navigation`.

> The project is intentionally lightweight: distro data comes from local JSON files, images are served as static assets, and there is no backend or database.

---

![Home page on desktop](screens/homepage.png)
![Distro detail page on desktop](screens/distro-detail.png)
![Distro comparison selection on desktop](screens/compare-select.png)
![Distro comparison page on desktop](screens/compare-page.png)
![Distro recommendation wizard on desktop](screens/wizard-1.png)
![Distro recommendation wizard on desktop](screens/wizard-2.png)
![Distro recommendation wizard on desktop](screens/wizard-results.png)

| ![Home page on mobile](screens/homepage-mobile.png) | ![Distro detail page on mobile](screens/distro-detail-mobile-1.png) | ![Distro detail page on mobile](screens/distro-detail-mobile-2.png) |
| --- | --- | --- |

## ✨ Features

### 🗂️ Browse and Filter Distros

- Browse a card grid of Linux distributions from a static data set
- Search by name, description, desktop environment, or base distro
- Filter by desktop, category, and base distro
- Sort by name, popularity, or last update
- Keep filters synced with the URL query string for easy sharing

### 📄 Distro Detail Pages

- Dynamic route at `/distro/[slug]`
- Pre-generated with `generateStaticParams()`
- Rich overview with description, metadata, homepage link, and imagery
- Clickable desktop and category tags that take you back to filtered results
- Breadcrumb navigation for quick return to the main listing

### ↔️ Comparison Workflow

- Select up to **3** distributions from the home grid
- Compare them on a dedicated route: `/compare?distros=ubuntu,mint`
- Remove distros directly from the comparison view without starting over

### 🧭 Recommendation Wizard

- Multi-step recommendation flow at `/wizard`
- Asks about experience level, use case, hardware, priorities, desktop preferences, package manager, and init system when relevant
- Scores distros client-side and explains why a match was recommended
- Saves progress in local storage so a session can be resumed

### 🎨 UI and Styling

- Custom CSS-based design system
- Reusable UI primitives for badges, tags, definition rows, and radio groups
- Responsive layouts for grid, detail, compare, and wizard screens

---

## 🧱 Tech Stack

- **Next.js 16** with the **App Router**
- **React 19** and **TypeScript**
- **next/image** and **next/link** for optimized app navigation and media
- **Vitest** + Testing Library for unit testing
- **ESLint** with the Next.js ruleset

---

## 🗺️ Routes

- `/` → distro grid, filtering, and compare selection
- `/distro/[slug]` → distro detail page
- `/compare?distros=slug1,slug2` → side-by-side comparison
- `/wizard` → recommendation wizard

---

## 🧱 Project Structure

```text
src/
├── app/                 # Next.js App Router pages and layout
│   ├── compare/
│   ├── distro/[slug]/
│   └── wizard/
├── components/          # Feature and UI components
├── context/             # Shared distro data provider
├── data/                # distros.json and lookup/filter services
├── hooks/               # Next navigation + URL/search helpers
├── styles/              # Global and feature-specific CSS
├── test/                # Vitest setup and unit tests
├── types/               # Shared TypeScript interfaces
└── utils/               # Scoring, filters, categories, storage
```

---

## ⚙️ Data and Architecture

- Distro data lives in `src/data/distros.json`
- Selector and filter logic lives in `src/data/distroService.ts`
- Shared access to distro data is provided through `DistroContext`
- URL state is managed with custom hooks built on `next/navigation`
- Wizard recommendations are computed in `src/utils/scoring.ts`

---

## 🚀 Getting Started

### Prerequisites

- Node.js **20+**
- npm

### Install dependencies

```bash
npm install
```

### Start the development server

```bash
npm run dev
```

Open:

```text
http://localhost:3000
```

### Production build

```bash
npm run build
npm run start
```

### Helpful scripts

```bash
npm run lint
npm run test
npm run test:run
npm run test:ui
```

---

## ❌ Not Included

- No backend API
- No authentication system
- No database
- No analytics or user accounts

The app is designed to stay easy to understand, fast to run locally, and simple to extend.

---

## 🤝 Contributing

Contributions, fixes, and content improvements are welcome.

---

## 📄 License

See the [LICENSE](LICENSE) file for details.
