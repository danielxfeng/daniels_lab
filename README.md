# Daniel's Lab

Daniel’s Lab was built with a couple of proposes. First, it’s my **personal portfolio website**, a place to show what I’ve been working on. It’s also a **central hub** where I keep all of my projects in one place.

On top of that, I wanted somewhere to share what I’ve learned along the way. So I put together a **blog management system**.

---

![Screenshot](https://github.com/danielxfeng/daniels_lab_frontend_react/raw/main/public/Screenshot.jpg)

---

## **Features**

### Frontend

- **Particle Gravity**  
  To keep the site from feeling too boring, I added a lightweight particle system, basically a tiny background “mini‑game” on the homepage.

- **Seamless Authentication**  
  Sign‑ins use silent token refresh, and refresh tokens are bound to a device fingerprint for extra security. Sessions stay active without constant logins. (And still without cookies)

- **Full‑Text Search with Local Suggestions**  
  The search lets you do full text queries and also suggests results based on local search history for a more personal touch.

- **Blog Filtering with Debounced Auto‑Submit**  
  Blog filters auto‑submit when users input stops changing for a moment (no extra button clicks needed).

- **Animations**  
  Some animations make the site feel alive, hopefully not too much, though. 🙂

- **Tag Input with Throttle and Drag‑to‑Delete**  
  When creating or updating posts, the tag selector shows real time suggestions with throttling and debouncing, plus responsive drag‑to‑delete interactions. (Unfortunately, this one’s admin‑only — just for me 🙂)

### Backend

- **Modular and Stateless Design**  
  The backend is split into independent modules, authentication and blog APIs can be separated and fully stateless. This makes it easy to scale or even split them into microservices in the future if needed.

- **Authentication from Scratch**  
  Built a custom authentication module from scratch, supporting both password login and multiple OAuth providers (Google, GitHub, LinkedIn).  
  Implemented a dual‑token system with refresh tokens following a rotation policy: each refresh token is valid for a single use only.

- **Pluggable Full‑Text Search (Elasticsearch / Meilisearch)**  
  Full text search is abstracted behind a unified interface, so the engine can be swapped out easily. (I first built it with Elasticsearch, but my tiny VPS couldn’t handle its memory usage.)

- **User Data Validation Middleware**  
  Requests are validated upfront with a validation middleware, ensuring consistent and secure data handling across all API endpoints.

### Deployment

- **CI/CD Pipeline**  
  Pushing to `main` runs the full test suite and, if all checks pass, deploys automatically. This keeps releases frequent and low‑risk — no manual steps, no surprises.

- **Hybrid SaaS + VPS Architecture**  
  The frontend runs on **Vercel**, the database lives on **Neon**, and the backend plus search services are deployed to a lightweight **Azure VPS**. Everything sits behind **Cloudflare**, giving unified routing and security without extra complexity.

- **One‑Command VPS Provisioning**  
  Built a custom script to configure the VPS from scratch: install dependencies, set up services, and even switch providers or scale up with a single command.

## Tech Stack

**Frontend**
- React 19 with React Router 7
- Zustand for state management
- React Hook Form + Zod for form handling and validation
- Tailwind CSS 4 for styling and theming
- ShadCN UI component library
- Framer Motion for animations
- Custom particle system built with Three.js and React Three Fiber (R3F)
- Drag‑and‑drop interactions with @dnd-kit

**Backend**
- Node.js
- PostgreSQL
- Custom Auth with JWT and OAuth2 (Google/GitHub/LinkedIn)
- Full‑text search with pluggable engines (Elasticsearch / Meilisearch)
- Middleware‑based request validation

**Infrastructure**
- Vercel (frontend hosting)
- Neon (PostgreSQL database)
- Azure VPS (backend & search)
- Cloudflare (routing & security)
- GitHub Actions (CI/CD with submodule auto‑update)

## **Repository Structure**

This repo includes the following submodules:

- **`frontend_react/`**  
  A modern React-based frontend, implementing the main user interface with routing, SEO, and interactive components.

- **`backend_node/`**  
  A Node.js (Express/Fastify) backend providing RESTful APIs, authentication, and blog management services.

- **`web_deployment/`**  
  Deployment configuration and scripts for production environments (e.g., Docker, CI/CD pipelines).

---
