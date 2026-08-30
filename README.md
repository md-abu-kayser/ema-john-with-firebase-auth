# Ema-John - React + TypeScript + Vite Shopping App (Firebase Auth & Hosting)

<!-- MIT License -->

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)

<!-- HTML & CSS -->

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)

<!-- Styling / PostCSS -->

[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?logo=tailwindcss&logoColor=white)](https://tailwindcss.com/docs/)
[![PostCSS](https://img.shields.io/badge/PostCSS-efefef?logo=postcss&logoColor=black)](https://postcss.org/)

<!-- Infra & Runtime -->

[![Node.js](https://img.shields.io/badge/Node.js-339933?logo=node.js&logoColor=white)](https://nodejs.org/)
[![Express](https://img.shields.io/badge/Express-000000?logo=express&logoColor=white)](https://expressjs.com/)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)

<!-- Languages & Web Standards -->

[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![ECMAScript Spec](https://img.shields.io/badge/ECMAScript-262-7A0BC0?logo=ecmascript&logoColor=white)](https://www.ecma-international.org/publications-and-standards/standards/ecma-262/)
[![TypeScript](https://img.shields.io/badge/TypeScript-3178c6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/docs/)

<!-- Auth & Security -->

[![Firebase](https://img.shields.io/badge/Firebase-FFCA28?logo=firebase&logoColor=black)](https://firebase.google.com/docs)
[![Passport.js](https://img.shields.io/badge/Passport.js-4B2B8D?logo=passport.js&logoColor=white)](http://www.passportjs.org/)
[![Auth0](https://img.shields.io/badge/Auth0-EB5424?logo=auth0&logoColor=white)](https://auth0.com/)

<!-- Testing -->

[![Jest](https://img.shields.io/badge/Jest-C21325?logo=jest&logoColor=white)](https://jestjs.io/)

<!-- Linting & Formatting -->

[![ESLint](https://img.shields.io/badge/ESLint-4B32C3?logo=eslint&logoColor=white)](https://eslint.org/docs/latest/)
[![Prettier](https://img.shields.io/badge/Prettier-2B3A42?logo=prettier&logoColor=white)](https://prettier.io/docs/)

<!-- Bundler -->

[![Vite](https://img.shields.io/badge/Vite-646cff?logo=vite&logoColor=white)](https://vite.dev/)

---

A production‑ready, modular e‑commerce demo application built with React, TypeScript, Vite, Tailwind CSS and Firebase (Authentication + Hosting). This repository demonstrates modern frontend architecture, client-side state + persistence, routing, and a deployment pipeline to Firebase Hosting.

## Quick links

- [package.json](package.json) - scripts & dependencies
- [index.html](index.html) - app entry HTML
- [`main`](src/main.tsx) - bootstrap / root renderer ([src/main.tsx](src/main.tsx))
- [`App`](src/App.tsx) - top-level application component ([src/App.tsx](src/App.tsx))
- [Global styles](src/index.css) - Tailwind + base styles ([src/index.css](src/index.css))
- [Component styles](src/App.css) - component-level styles ([src/App.css](src/App.css))
- [Firebase configuration](firebase.json) - hosting config ([firebase.json](firebase.json))
- [.gitignore](.gitignore) - repository ignores
- [Tailwind config](tailwind.config.js) - Tailwind customization
- [Vite config](vite.config.ts) - build/dev configuration

## Key features

- Modern React 18 + TypeScript codebase.
- Fast development with Vite and HMR ([vite](https://vitejs.dev/), see [package.json](package.json) scripts).
- Tailwind CSS utility-first styling with custom base ([src/index.css](src/index.css)) and PostCSS configuration.
- Firebase:
  - Authentication flows (Login / SignUp) and protected routes.
  - Hosting-ready configuration ([firebase.json](firebase.json)) pointing to build output `dist`.
- Client-side cart persistence with LocalForage and utilities for product search (match-sorter).
- Componentized UI: [src/components](src/components) covering Cart, Checkout, Inventory, Header, Layout, Login, Orders, Product, ReviewItem, Shop, SignUp.
- Sample product data for local development: [public/products.json](public/products.json) and [src/fakeData/products.json](src/fakeData/products.json).
- FontAwesome integration for icons.

## Getting started - local

1. **Install dependencies**

```bash
   npm install
```

2. **Run dev server**

```bash
   npm run dev
```

- Uses the `dev` script in [package.json](package.json)

3. **Build for production**

```bash
   npm run build
```

4. **Preview production build locally**

```bash
   npm run preview
```

## Recommended Workflow

- Use branches for features and PRs.
- Run the dev server while developing components in [src/components](src/components).
- Keep global styles in [src/index.css](src/index.css) and utility CSS in [src/App.css](src/App.css).

## Firebase hosting - deployment

- The hosting configuration uses `dist` as the public directory - see [firebase.json](firebase.json).
- Common deployment steps:
  1. Build: npm run build
  2. Login to Firebase CLI: firebase login
  3. Select project: firebase use --add
  4. Deploy hosting: firebase deploy --only hosting
     "If you use the included `.firebaserc` ensure it points to the correct Firebase project."

## Project structure - Top High Level

- src/
  - main.tsx - app bootstrap ([src/main.tsx](src/main.tsx))
  - App.tsx - root component ([src/App.tsx](src/App.tsx))
  - index.css, App.css - styling ([src/index.css](src/index.css)) ([src/App.css](src/App.css))
  - components/ - feature/components (Cart, Checkout, Shop, Product, Header, etc.)
  - fakeData/products.json - dev product fixtures ([src/fakeData/products.json](src/fakeData/products.json))
  - firebase/ - Firebase helper modules (auth, config)
- public/ - static assets ([public/products.json](public/products.json), favicon)
- build output: dist (generated by `npm run build`)

## Dependencies - high level

- react, react-dom, react-router-dom
- typescript, vite, @vitejs/plugin-react
- tailwindcss, postcss, autoprefixer
- firebase
- localforage, match-sorter, font awesome

### Development Tips

- Inspect the app entry in [index.html](index.html) and the script path for main ([index.html](index.html)).
- Tailwind utilities are configured via [tailwind.config.js](tailwind.config.js).
- Use the browser DevTools to emulate auth flows and local storage persistence.

### Contributing

- Fork - feature branch - PR with a clear description and screenshots.
- Keep changes small and focused; add unit tests where applicable.
- Follow existing code patterns and TypeScript types.

### Acknowledgements

- Built with Vite, React, TypeScript, Tailwind CSS and Firebase.
- Sample dataset and app idea inspired by common e‑commerce tutorials.

### License

- This project is licensed under the terms of the **[MIT License](./LICENSE)**.
- You may replace or update the license as needed for client or proprietary projects.

---

### Contact & Maintainer

- **Name:** Md Abu Kayser - Full-Stack Engineer
- **Project:** _ema-john-vite-firebase_
- **Maintainer:** [md-abu-kayser](https://github.com/md-abu-kayser)
- **GitHub:** [github.com/abu.kayser-official](https://github.com/md-abu-kayser)
- **Email:** [abu.kayser.official@gmail.com](mailto:abu.kayser.official@gmail.com)

---

If you’d like this README tailored for a specific purpose - such as **hiring managers**, **open-source contributors**, or **client deliverables** - feel free to request a custom tone or format.

---

**Thank you for reviewing this project!**

---
