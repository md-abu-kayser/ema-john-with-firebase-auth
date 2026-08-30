# Ema-John

<p align="center">
  <strong>React + TypeScript E-Commerce Frontend</strong>
</p>

<p align="center">
  A modern storefront application built with <strong>React 18, TypeScript, Vite, Tailwind CSS, Firebase Authentication, and Firebase Hosting</strong>.
</p>

<p align="center">
  The project demonstrates reusable component architecture, client-side routing,
  authenticated user flows, persistent shopping state, product search,
  responsive UI design, and a deployment-ready frontend workflow.
</p>

<p align="center">
  <a href="https://github.com/md-abu-kayser/ema-john-vite-firebase">
    <img src="https://img.shields.io/badge/GitHub-Repository-181717?style=for-the-badge&logo=github" alt="GitHub Repository" />
  </a>
  <a href="./LICENSE">
    <img src="https://img.shields.io/badge/License-MIT-2563EB?style=for-the-badge" alt="MIT License" />
  </a>
  <img src="https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=111827" alt="React 18" />
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white" alt="Vite" />
  <img src="https://img.shields.io/badge/Firebase-Authentication%20%2B%20Hosting-FFCA28?style=for-the-badge&logo=firebase&logoColor=111827" alt="Firebase" />
</p>

<p align="center">
  <a href="#overview">Overview</a> •
  <a href="#features">Features</a> •
  <a href="#architecture">Architecture</a> •
  <a href="#tech-stack">Tech Stack</a> •
  <a href="#getting-started">Getting Started</a> •
  <a href="#firebase">Firebase</a> •
  <a href="#deployment">Deployment</a> •
  <a href="#roadmap">Roadmap</a>
</p>

---

# Overview

**Ema-John** is a modern e-commerce frontend built with React and TypeScript.

The project focuses on the client-side shopping experience and demonstrates how a storefront can be structured around reusable components, route-based navigation, authentication, local persistence, and static product data.

The application currently combines:

```text
React
+
TypeScript
+
Vite
+
Tailwind CSS
+
Firebase Authentication
+
Firebase Hosting
+
LocalForage
+
Match Sorter
```

The goal is to provide a clean foundation for a storefront while keeping the architecture simple enough to understand and extend.

---

# Project Goals

The project is designed around several practical frontend engineering goals.

## Component Reusability

Organize the interface into focused components rather than building the application around a monolithic page.

## Type Safety

Use TypeScript to make component and application contracts clearer and safer.

## Authentication

Provide authenticated user flows using Firebase Authentication.

## Persistent Client State

Preserve shopping-related state using browser-side persistence.

## Search Experience

Provide a more useful product discovery experience using search utilities.

## Deployment Readiness

Use Vite to produce a production build that can be deployed through Firebase Hosting.

---

# Features

## 🛒 Shopping Experience

The application provides a storefront-oriented interface with product discovery and shopping-related UI.

The component structure includes areas such as:

```text id="w3r1s2"
Shop
Products
Product
Cart
Checkout
Orders
Reviews
```

These components form the primary product experience layer.

---

## 🔐 Firebase Authentication

The project integrates Firebase Authentication for authenticated user workflows.

The current application includes:

- Login
- Sign up
- Protected application flows
- Authentication-aware UI

Firebase provides the identity layer while the React application consumes the resulting authentication state.

Conceptually:

```text id="n7m9xo"
User
  ↓
Login / Sign Up
  ↓
Firebase Authentication
  ↓
Authenticated Session
  ↓
React Application
```

---

# Protected Application Areas

Authenticated routes can be used to restrict access to areas such as:

```text id="s0j1n4"
Protected
├── Cart
├── Checkout
└── Orders
```

The exact route structure should remain synchronized with the current router configuration.

The project documentation identifies authentication and protected-route behavior as part of the application's capabilities.

---

# 🧾 Shopping Cart Persistence

Cart-related state is persisted on the client using **LocalForage**.

Conceptually:

```text id="d8mn32"
Product Selection
      ↓
Cart State
      ↓
LocalForage
      ↓
Browser Persistence
```

This allows shopping-related state to survive normal page refreshes without requiring a backend database.

For a full production commerce system, persistent carts would normally move to a backend or user-specific data store.

---

# 🔎 Product Search

The project includes `match-sorter` as a utility for product search/discovery.

The intended flow is:

```text id="0dkw93"
User Query
    ↓
Search Utility
    ↓
Product Filtering
    ↓
Matching Results
```

This keeps search logic separate from the visual presentation layer.

---

# 🎨 Tailwind CSS

Tailwind CSS provides the utility-first styling layer.

The application uses:

```text id="0h7sq8"
Tailwind CSS
      +
Custom Base Styles
      +
Component-Level Styling
```

Project styling is primarily organized through:

```text
src/index.css
src/App.css
tailwind.config.js
```

## The current documentation identifies these files as the main styling/configuration points.

# 🧩 Feature-Oriented Components

The application separates major storefront responsibilities into dedicated components.

Current documented areas include:

```text id="gc2a9w"
components/
├── Cart
├── Checkout
├── Inventory
├── Header
├── Layout
├── Login
├── Orders
├── Product
├── ReviewItem
├── Shop
└── SignUp
```

This provides a clear starting point for future feature growth.

---

# Architecture

## High-Level Architecture

```text id="r2ty2p"
┌─────────────────────────────────────────────────────┐
│                  React Frontend                    │
│                                                     │
│ Header │ Shop │ Product │ Cart │ Checkout │ Orders  │
└──────────────────────────┬──────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────┐
│                Application Layer                   │
│                                                     │
│ Routing │ Component State │ Auth State │ Search     │
└───────────────┬──────────────────┬──────────────────┘
                │                  │
                ▼                  ▼
       ┌────────────────┐   ┌─────────────────────┐
       │ Firebase Auth  │   │ Local Client State  │
       │                │   │                     │
       │ Identity       │   │ LocalForage         │
       └────────────────┘   └─────────────────────┘
                │
                ▼
       ┌────────────────────┐
       │ Static Product Data│
       │ JSON               │
       └────────────────────┘
```

---

# Architecture Principles

## Separation of Concerns

The application separates:

```text id="a1v5ty"
Presentation
   ≠
Authentication
   ≠
Product Data
   ≠
Client Persistence
```

This makes each area easier to maintain.

---

## Reusable Components

Shared behavior should be implemented once and reused across pages where possible.

For example:

```text id="h4h8ec"
ProductCard
   ↓
Shop
   ↓
Search Results
   ↓
Product Listing
```

---

## Data-Driven Product Rendering

Products are represented as JSON rather than hard-coded repeatedly throughout the UI.

Current datasets are documented in:

```text id="bzg2kk"
public/products.json
src/fakeData/products.json
```

This makes it straightforward to replace the local source with an API in the future.

---

# Authentication Architecture

The authentication system can be understood as:

```text id="qczw3m"
React Application
       ↓
Auth Logic
       ↓
Firebase
       ↓
Current User
       ↓
Application State
       ↓
Protected UI
```

A future application-specific backend can sit behind this identity layer.

---

# Authentication Lifecycle

```text id="fcw8q3"
Application Start
       ↓
Initialize Firebase
       ↓
Resolve Current Session
       ↓
Update Auth State
       ↓
Render Application
```

This prevents the rest of the application from needing to independently determine authentication state.

---

# Data Architecture

The project currently has two important data categories.

## Product Data

Static JSON:

```text id="t5i5c0"
public/products.json
src/fakeData/products.json
```

## User / Shopping Data

Browser-side persistence through LocalForage.

Conceptually:

```text id="3kkg8k"
Products
   ↓
Shop
   ↓
Cart
   ↓
Local Persistence
   ↓
Checkout / Orders
```

---

# Future Data Architecture

A larger production implementation could evolve toward:

```text id="o1k6qp"
React Client
      ↓
API Service
      ↓
Backend
      ↓
Database
```

with Firebase continuing to provide authentication.

This would allow the application to support:

- Cross-device carts
- Persistent orders
- Inventory synchronization
- User profiles
- Product management
- Server-side business rules

---

# Tech Stack

## Frontend

| Technology   | Purpose                       |
| ------------ | ----------------------------- |
| React 18     | Component-based UI            |
| TypeScript   | Type-safe development         |
| Vite         | Development and build tooling |
| React Router | Client-side routing           |
| Tailwind CSS | Utility-first styling         |

---

## Authentication & Infrastructure

| Technology              | Purpose                          |
| ----------------------- | -------------------------------- |
| Firebase Authentication | User identity and authentication |
| Firebase Hosting        | Static frontend deployment       |

The project documentation explicitly identifies Firebase for authentication and Hosting configuration.

---

## Client Utilities

| Technology   | Purpose                      |
| ------------ | ---------------------------- |
| LocalForage  | Persistent browser-side data |
| Match Sorter | Product search/filtering     |
| Font Awesome | Icons                        |

---

# Repository Structure

```text id="07izl5"
ema-john-vite-firebase/
│
├── public/
│   ├── products.json
│   ├── favicon/
│   └── ...
│
├── src/
│   │
│   ├── components/
│   │   ├── Cart/
│   │   ├── Checkout/
│   │   ├── Header/
│   │   ├── Inventory/
│   │   ├── Layout/
│   │   ├── Login/
│   │   ├── Orders/
│   │   ├── Product/
│   │   ├── ReviewItem/
│   │   ├── Shop/
│   │   └── SignUp/
│   │
│   ├── fakeData/
│   │   └── products.json
│   │
│   ├── firebase/
│   │   └── Firebase-related helpers
│   │
│   ├── App.tsx
│   ├── App.css
│   ├── index.css
│   └── main.tsx
│
├── firebase.json
├── .firebaserc
├── package.json
├── tailwind.config.js
├── vite.config.ts
├── tsconfig.json
├── .gitignore
├── LICENSE
└── README.md
```

The important project files and major feature areas are reflected from the supplied repository documentation.

---

# Core Files

## `src/main.tsx`

Application bootstrap.

Responsible for mounting the React application into the browser.

---

## `src/App.tsx`

Top-level application composition and route integration.

---

## `src/index.css`

Global styling and Tailwind base integration.

---

## `src/App.css`

Application-level or component-specific styling.

---

## `firebase.json`

Firebase Hosting configuration.

The supplied project documentation identifies `dist` as the configured hosting directory.

---

# Getting Started

## Prerequisites

Install:

- Node.js
- npm
- Git
- Firebase project for authentication/hosting workflows

---

# 1. Clone Repository

```bash id="5j7gq1"
git clone https://github.com/md-abu-kayser/ema-john-vite-firebase.git
```

Enter the project:

```bash id="jbl7g5"
cd ema-john-vite-firebase
```

---

# 2. Install Dependencies

```bash id="bpt9y2"
npm install
```

---

# 3. Configure Firebase

Create the required environment configuration for the Firebase client.

Example:

```env id="nxom2r"
VITE_FIREBASE_API_KEY=your_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
VITE_FIREBASE_PROJECT_ID=your_project_id
VITE_FIREBASE_STORAGE_BUCKET=your_project.appspot.com
VITE_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
VITE_FIREBASE_APP_ID=your_app_id
```

Do not commit secrets or private server credentials.

---

# 4. Start Development

```bash id="apj0ob"
npm run dev
```

Vite will print the local development URL.

---

# Available Commands

| Command           | Purpose                  |
| ----------------- | ------------------------ |
| `npm run dev`     | Start development server |
| `npm run build`   | Create production build  |
| `npm run preview` | Preview production build |

The current repository documents these Vite commands as the core local development workflow.

---

# Development Workflow

Recommended workflow:

```text id="1fs5mj"
Create Feature Branch
        ↓
Implement Component / Feature
        ↓
Update Types / Data
        ↓
Run Application
        ↓
Verify Auth Flow
        ↓
Verify Responsive UI
        ↓
Build
        ↓
Commit
        ↓
Pull Request
```

---

# Firebase

## Authentication

Firebase Authentication manages the identity layer.

The frontend is responsible for:

```text id="j4e8ip"
Render Forms
     ↓
Call Firebase
     ↓
React to Auth State
     ↓
Update UI
```

---

## Hosting

The application uses Firebase Hosting for deployment.

The documented configuration points Firebase Hosting at:

```text id="q9b3l7"
dist/
```

---

# Deployment

## Build

Generate the production bundle:

```bash id="fjm8su"
npm run build
```

---

## Firebase CLI

Install the Firebase CLI if required:

```bash id="dhfwl6"
npm install -g firebase-tools
```

Authenticate:

```bash id="ui5vyd"
firebase login
```

Select the Firebase project:

```bash id="s5f1vy"
firebase use --add
```

Deploy:

```bash id="0ar3c1"
firebase deploy --only hosting
```

The project documentation describes this build → Firebase login → project selection → hosting deployment flow.

---

# Deployment Architecture

```text id="cr4dh0"
Developer
   ↓
git push
   ↓
Build
   ↓
npm run build
   ↓
dist/
   ↓
Firebase Hosting
   ↓
Users
```

---

# Production Considerations

The current project is a frontend application.

For a production commerce platform, the following concerns should eventually move to trusted backend infrastructure:

### Pricing

Do not rely on client-side calculations as the final source of truth.

### Inventory

Inventory should be validated server-side to avoid conflicting orders.

### Orders

Order creation should be persisted in a backend database.

### Payments

Payment operations should be handled through secure server-side integrations.

### Authorization

Frontend route protection should not be considered sufficient for sensitive backend operations.

---

# Security

## Environment Variables

Keep local configuration out of source control:

```text id="j7l1kl"
.env
.env.local
.env.production
```

Use an example configuration file where appropriate:

```text id="4y9dzs"
.env.example
```

---

## Firebase Client Configuration

Firebase client configuration may be present in frontend applications, but private service-account credentials must never be exposed to the browser.

---

## Client-Side Persistence

LocalForage is useful for browser-side state, but it should not be treated as a secure storage mechanism for sensitive information.

Do not store:

- Passwords
- Private credentials
- Payment secrets
- Server-side authorization secrets

in client storage.

---

# Accessibility

A professional storefront should maintain:

```text id="6c5g64"
Semantic HTML
     +
Keyboard Navigation
     +
Accessible Labels
     +
Visible Focus States
     +
Meaningful Error Messages
     +
Responsive Interaction
```

Future improvements can include automated accessibility testing with tools such as Lighthouse or axe.

---

# Performance

The Vite-based architecture provides a lightweight development and build experience.

Recommended production optimizations include:

- Image compression
- Lazy loading
- Route-level code splitting
- Optimized font loading
- Reduced JavaScript payload
- Browser caching
- CDN-backed static delivery

---

# Testing Strategy

A mature implementation should cover the most important application boundaries.

## Component Tests

Test reusable components such as:

- Product cards
- Cart UI
- Authentication forms
- Header
- Checkout

## Authentication Tests

Test:

```text id="g2oq99"
Login
Sign Up
Logout
Auth State
Protected Routes
```

## Commerce Tests

Test:

```text id="p0xxj4"
Product Rendering
Search
Cart State
Checkout
Order UI
```

---

# Recommended CI Pipeline

A future GitHub Actions pipeline can enforce:

```text id="l9i6jm"
Install
  ↓
Type Check
  ↓
Lint
  ↓
Test
  ↓
Build
```

A production repository should avoid merging changes that fail the required quality gates.

---

# API Migration Path

The current application uses static product data:

```text id="fc9jtm"
products.json
```

A future backend integration could replace it with:

```text id="6m7w6j"
GET /api/products
```

Then:

```text id="gz91rf"
React
  ↓
Product Service
  ↓
Backend API
  ↓
Database
```

This allows the current frontend to evolve without completely redesigning the UI layer.

---

# Future Commerce Architecture

```text id="v0cl0a"
                         React Client
                              │
                              ▼
                         API Gateway
                              │
          ┌───────────────────┼───────────────────┐
          ▼                   ▼                   ▼
       Products            Orders              Users
          │                   │                   │
          └───────────────────┼───────────────────┘
                              ▼
                           Database
                              │
                    ┌─────────┼─────────┐
                    ▼         ▼         ▼
                 Payment   Inventory  Analytics
```

This represents a possible future system architecture, not the current implementation.

---

# Roadmap

## Storefront

```text id="y8ct6w"
[ ] Advanced product search
[ ] Category filtering
[ ] Product detail pages
[ ] Wishlist
[ ] Improved checkout
[ ] Better order history
```

## Authentication

```text id="6ev5xx"
[x] Firebase Authentication
[x] Login
[x] Sign Up

[ ] Password reset
[ ] Email verification
[ ] Profile management
[ ] Improved session UX
```

## Backend

```text id="p5vhcp"
[ ] Product API
[ ] Persistent database
[ ] Server-side cart
[ ] Order API
[ ] Inventory service
[ ] Server-side authorization
```

## Payments

```text id="6pkqzz"
[ ] Payment gateway
[ ] Secure checkout
[ ] Payment verification
[ ] Refund workflow
```

## Engineering

```text id="b07h1i"
[ ] Automated unit tests
[ ] Integration testing
[ ] E2E testing
[ ] GitHub Actions CI
[ ] Automated deployment
[ ] Error monitoring
[ ] Performance monitoring
```

---

# Project Evolution

The project can evolve incrementally:

```text id="j5i6h6"
Static Product Data
       ↓
Firebase Authentication
       ↓
Persistent User State
       ↓
Backend API
       ↓
Database
       ↓
Orders & Inventory
       ↓
Payments
       ↓
Production Commerce Platform
```

This approach allows infrastructure to be introduced only when business requirements justify it.

---

# Code Quality Guidelines

When extending the project:

### Keep Components Focused

A component should have a clear responsibility.

### Prefer Reusability

Extract repeated UI patterns.

### Keep Product Data Separate

Do not embed large datasets directly inside components.

### Use TypeScript

Define explicit props and domain types.

### Keep Authentication Centralized

Do not duplicate Firebase auth logic across unrelated components.

### Validate Production Behavior

Always run the production build before deployment.

---

# Git Workflow

Recommended branch names:

```text id="u8i47t"
feature/product-search
feature/checkout-flow
feature/profile-page
feature/order-history
fix/auth-redirect
fix/cart-persistence
refactor/product-components
docs/readme-update
test/auth-components
```

---

# Commit Convention

Use Conventional Commit-style messages.

Examples:

```text id="0kv5vd"
feat(shop): add product search
feat(cart): persist cart with localforage
feat(auth): add protected checkout flow
fix(auth): handle firebase session loading
fix(products): correct search filtering
refactor(components): simplify product card
test(cart): add cart persistence coverage
docs(readme): improve deployment documentation
chore(deps): update frontend dependencies
ci(github): add build validation
```

Avoid vague commits such as:

```text id="7ar2q6"
update
changes
final
new code
fix stuff
```

---

# Pull Request Checklist

Before opening a PR:

```text id="al6i1u"
[ ] Feature is focused
[ ] TypeScript checks pass
[ ] Existing patterns are preserved
[ ] Authentication behavior verified
[ ] Responsive layout verified
[ ] Tests pass where configured
[ ] Production build succeeds
[ ] No secrets committed
[ ] Documentation updated
```

---

# Troubleshooting

## Firebase Authentication Fails

Check:

```text id="7m8x2m"
[ ] Firebase project ID
[ ] Authentication providers enabled
[ ] Environment variables loaded
[ ] Authorized domains configured
[ ] Browser console
```

---

## Products Are Not Displaying

Check:

```text id="5g4c9s"
[ ] public/products.json exists
[ ] JSON is valid
[ ] Product fields match component expectations
[ ] Network request succeeds
[ ] Browser console has no errors
```

---

## Production Build Fails

Run:

```bash id="7k2gth"
npm install
npm run build
```

Then inspect:

- TypeScript errors
- Import paths
- Missing modules
- Environment configuration
- Firebase initialization

---

# What This Project Demonstrates

From a portfolio perspective, this repository demonstrates:

## React

- Component architecture
- Application composition
- Reusable UI
- State-driven interfaces

## TypeScript

- Typed application development
- Component contracts
- Refactoring safety

## Firebase

- Authentication
- Hosting
- Frontend cloud integration

## E-Commerce UX

- Product browsing
- Search
- Cart
- Checkout
- Orders
- Authentication

## Frontend Engineering

- Responsive design
- Persistent client state
- Static deployment
- Build tooling
- Structured feature organization

---

# Why This Project Matters

The strongest aspect of Ema-John is not simply that it looks like a storefront.

It demonstrates a progression from:

```text id="k6n8z8"
UI
 ↓
Components
 ↓
State
 ↓
Authentication
 ↓
Persistence
 ↓
Deployment
```

with a clear path toward:

```text id="sgj3jn"
Frontend
 ↓
API
 ↓
Database
 ↓
Commerce Infrastructure
```

That makes the project useful as both a portfolio artifact and a foundation for future engineering work.

---

# Current Scope

The current repository should primarily be understood as a **React + TypeScript frontend application with Firebase Authentication and Hosting integration**.

Current core infrastructure includes:

```text id="3m7q4h"
React 18
TypeScript
Vite
Tailwind CSS
Firebase Authentication
Firebase Hosting
LocalForage
Match Sorter
```

The project documentation identifies local product datasets and browser-side persistence as part of the current implementation.

A full backend-driven commerce system remains a natural next stage rather than an assumption about the current codebase.

---

# Documentation Resources

### React

https://react.dev/

### TypeScript

https://www.typescriptlang.org/docs/

### Vite

https://vite.dev/

### Tailwind CSS

https://tailwindcss.com/docs/

### Firebase

https://firebase.google.com/docs

### React Router

https://reactrouter.com/

### LocalForage

https://localforage.github.io/localForage/

### Match Sorter

https://github.com/kentcdodds/match-sorter

### Jest

https://jestjs.io/

### ESLint

https://eslint.org/

### Prettier

https://prettier.io/

---

# License

This project is licensed under the **MIT License**.

See the [LICENSE](./LICENSE) file for complete details.

---

# Maintainer

<p align="center">
  <strong>Md Abu Kayser</strong>
</p>

<p align="center">
  Full-Stack Engineer
</p>

<p align="center">
  <a href="https://github.com/md-abu-kayser">
    GitHub
  </a>
  •
  <a href="mailto:abu.kayser.official@gmail.com">
    Email
  </a>
</p>

For collaboration, technical discussions, portfolio reviews, or professional opportunities, please reach out through GitHub or email.

---

# Project Information

| Property           | Details                  |
| ------------------ | ------------------------ |
| Project            | Ema-John                 |
| Repository         | `ema-john-vite-firebase` |
| Type               | E-Commerce Frontend      |
| Frontend           | React 18 + TypeScript    |
| Build Tool         | Vite                     |
| Styling            | Tailwind CSS             |
| Authentication     | Firebase Authentication  |
| Hosting            | Firebase Hosting         |
| Client Persistence | LocalForage              |
| Search             | Match Sorter             |
| License            | MIT                      |
| Maintainer         | Md Abu Kayser            |

---

<p align="center">
  <a href="#ema-john">⬆ Back to top</a>
</p>

<p align="center">
  <strong>Build the storefront. Keep the architecture clean. Ship with confidence.</strong>
</p>

<p align="center">
  Built with React, TypeScript, Vite, Firebase, and a focus on maintainable frontend engineering.
</p>
