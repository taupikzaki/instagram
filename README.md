# instagram
Ini adalah tutorial membuat instagram di React JS


## Create Project
```
npm create vite@latest .
```
```
npm install
```
## Delete Src and create again

## create main.tsx in src folder
```
import ReactDOM from "react-dom/client";
import App from "./App";

ReactDOM.createRoot(document.getElementById("root")!).render(<App />);
```
## Create App.tsx
```
import React from "react";

const App = () => {
  return <div>App</div>;
};

export default App;
```

## Install tailwind
https://tailwindcss.com/docs/installation/using-vite  

## Di globals css isi berikut
```
@import "tailwindcss";
@custom-variant dark (&:where(.dark, .dark *));

/* Warna kustom */
@theme {
  --color-primary-500: #877eff;
  --color-primary-600: #5d5fef;
  --color-secondary-500: #ffb620;
  --color-off-white: #d0dfff;
  --color-red: #ff5a5a;
  --color-dark-1: #000000;
  --color-dark-2: #09090a;
  --color-dark-3: #101012;
  --color-dark-4: #1f1f22;
  --color-light-1: #ffffff;
  --color-light-2: #efefef;
  --color-light-3: #7878a3;
  --color-light-4: #5c5c7b;

  --font-inter: "Inter", sans-serif;
}
/* Costum Width */
.w-420 {
  width: 420px;
}
.w-465 {
  width: 465px;
}

@media (min-width: 480px) {
  .xs\:text-base {
    font-size: 1rem;
  } /* contoh */
}
/* Animate */
@keyframes accordion-down {
  from {
    height: 0;
  }
  to {
    height: var(--radix-accordion-content-height);
  }
}

@keyframes accordion-up {
  from {
    height: var(--radix-accordion-content-height);
  }
  to {
    height: 0;
  }
}

.animate-accordion-down {
  animation: accordion-down 0.2s ease-out;
}

.animate-accordion-up {
  animation: accordion-up 0.2s ease-out;
}
```
## Install
```
bun add react-router-dom
```
## Install Shadcn
```
https://ui.shadcn.com/docs/installation/vite
```
