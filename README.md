# instagram
Ini adalah tutorial membuat instagram di React JS


## Create Project
```
bun create vite@4.4.1 .
```
```
bun install
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

## Install tailwind v3 supaya tidak error dan baca dokumentasi
https://v3.tailwindcss.com/docs/guides/vite
setelah itu import
```
import "./globals.css";
```
