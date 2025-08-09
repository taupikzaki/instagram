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

- _auth

src > _auth > AuthLayout.tsx  

```
import { Navigate, Outlet } from "react-router-dom";

const AuthLayout = () => {
  const isAuthenticated = false;
  return (
    <>
      {isAuthenticated ? (
        <Navigate to="/" />
      ) : (
        <>
          <section className="flex flex-1 justify-center items-center flex-col py-10">
            <Outlet />
          </section>
        </>
      )}
    </>
  );
};

export default AuthLayout;
```
src > _auth > forms > SigninForm.tsx  
src > _auth > forms > SignupForm.tsx  
install shadcn form component
```
npx shadcn@latest add form
```
install shadcn input component
```
npx shadcn@latest add input
```

- _root

src > _root > Rootlayout.tsx  
src > _root > pages > Home.tsx  
src > _root > pages > index.ts
```
export { default as Home } from "./Home";
```
- app.tsx

```
import { Route, Routes } from "react-router-dom";
import SigninForm from "./_auth/forms/SigninForm";
import SignupForm from "./_auth/forms/SignupForm";
import { Home } from "./_root/pages";
import AuthLayout from "./_auth/AuthLayout";
import RootLayout from "./_root/RootLayout";

const App = () => {
  return (
    <main className="flex h-screen">
      <Routes>
        {/* Public Routes */}
        <Route element={<AuthLayout />}>
          <Route path="/sign-in" element={<SigninForm />} />
          <Route path="/sign-up" element={<SignupForm />} />
        </Route>

        {/* Private Routes */}
        <Route element={<RootLayout />}>
          <Route index element={<Home />} />
        </Route>
      </Routes>
    </main>
  );
};

export default App;
```
