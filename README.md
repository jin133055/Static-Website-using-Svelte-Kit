# Static Website using Svelte kit
This is a static website for a fictional Tech Conference, built using SvelteKit and Sveltestrap (Bootstrap for Svelte). The website includes multiple pages, a dark mode toggle, and responsive design.
# Setup & Installation
## Installing SvelteKit
```
npm create svelte@latest tech-conference
cd tech-conference
npm install
```
# sv
Everything you need to build a Svelte project, powered by [`sv`](https://github.com/sveltejs/cli).
## Creating a project
If you're seeing this, you've probably already done this step. Congrats!
```bash
# create a new project in the current directory
npx sv create
# create a new project in my-app
npx sv create my-app
```
# Project Structure
```
tech-conference/
├── src/
│   ├── routes/
│   │   ├── +layout.svelte  # Main layout
│   │   ├── +page.svelte    # Home page
│   │   ├── about/+page.svelte
│   │   ├── contact/+page.svelte
│   │   ├── schedule/+page.svelte
│   │   ├── speakers/+page.svelte
│   │   ├── sponsors/+page.svelte
│   ├── app.css             # Global styles
│   ├── lib/                # Reusable components
│
├── static/                 # Static assets (images, fonts, etc.)
├── package.json
├── svelte.config.js
└── README.md
```
#  Adding Pages
I created different pages inside src/routes/. Each page is a Svelte file with its own +page.svelte.

## Developing
Once you've created a project and installed dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:
```bash
npm run dev
# or start the server and open the app in a new browser tab
npm run dev -- --open
```
## Building
To create a production version of your app:
```bash
npm run build
```
# Final Thoughts
This project uses SvelteKit for fast performance.
Fully responsive and accessible.
You can preview the production build with `npm run preview`.
> To deploy your app, you may need to install an [adapter](https://svelte.dev/docs/kit/adapters) for your target environment.
