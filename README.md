<h1 align="center">Membuat Instagram Clone</h1>

<h3 align="center">Instal React JS via Vite</h3>  

```
npm create vite@latest .
```
**Note:** Pilih framework React, pilih variant Typescript

<h3 align="center">Install tailwind</h3>
https://tailwindcss.com/docs/installation/using-vite

<h3 align="center">Instal Shadcn</h3>
https://ui.shadcn.com/docs/installation/vite

<h3 align="center">Instal React Router Dom</h3>

```
npm install react-router-dom
```

<h3 align="center">Install Appwrite</h3>

```
npm install appwrite
```

<h3 align="center">main.tsx</h3>
src > main.tsx

```
import ReactDOM from "react-dom/client";
import { BrowserRouter } from "react-router-dom";
import App from "./App";

ReactDOM.createRoot(document.getElementById("root")!).render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);
```

<h3 align="center">app.tsx</h3>
src > app.tsx
