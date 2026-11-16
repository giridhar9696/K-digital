# Kubera Media UI source

The public site is made of static HTML files. Shared styles live in `styles.css`. The React/TypeScript components live in `components/ui/` and `components/ui/index.tsx` mounts them into the existing pages. Serve this directory with any static server to use the built site.

```sh
npm ci
npm run typecheck
npm run build
npm test
```

The build writes `assets/ui.js`. Include it when publishing the static pages.

About's Horizontal Feature Reveal uses GSAP ScrollTrigger and SplitText for desktop scroll. Tablets, phones, and reduced-motion settings show the same content in a vertical layout. The Blog gallery uses native CSS sticky positioning. Both components share the site's CSS, so their React source works with the current build.

The site uses its own CSS and does not require Tailwind or shadcn to run. To create a shadcn project for these components, use `npx shadcn@latest init --template vite` in a separate project directory, then follow the [Vite setup](https://ui.shadcn.com/docs/installation/vite) to configure Tailwind and the `@/` alias. Choose the React and TypeScript setup. For an existing Vite app, install Tailwind with `npm install tailwindcss @tailwindcss/vite` and run `npx shadcn@latest init` after configuring the Tailwind plugin and import. If TypeScript is missing, install it with `npm install -D typescript @types/react @types/react-dom` and use the React JSX and bundler settings in this project's `tsconfig.json`.

Keep the portable components in `components/ui/` and point the shadcn UI alias at that directory. Registry components and examples use the alias to import shared UI without depending on a page's location. Keep the component styles from `styles.css` in the consuming project's global stylesheet.

# K-digital
