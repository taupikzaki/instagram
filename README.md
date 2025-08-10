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

### src > _auth > AuthLayout.tsx

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
### src > _auth > forms > SignupForm.tsx  
install shadcn form component
```
npx shadcn@latest add form
```
install shadcn input component
```
npx shadcn@latest add input
```
buat sign-up validation

src > lib > validation > index.ts
```
import { z } from "zod";

export const SignupValidation = z.object({
  name: z.string().min(2, { message: "Name must be at least 2 characters." }),
  username: z
    .string()
    .min(2, { message: "Name must be at least 2 characters." }),
  email: z.string().email(),
  password: z
    .string()
    .min(8, { message: "Password must be at least 8 characters." }),
});
```

buat Loader untuk mempercantik tampilan loading

src > components > shared > Loader.tsx
```
const Loader = () => {
  return (
    <div className="flex-center w-full">
      <img src="/assets/icons/loader.svg" alt="loader" width={24} height={24} />
    </div>
  );
};

export default Loader;
```

Setting Appwrite

create file **.env.local** di root
```
VITE_APPWRITE_PROJECT_ID="6896b57900099e1d6539"
VITE_APPWRITE_URL="https://nyc.cloud.appwrite.io/v1"
```
buat file vite environment
src > vite-env.d.ts
```
/// <reference types="vite/client"/>
```

src > lib > appwrite > config.ts
```
import { Client, Account, Databases, Storage, Avatars } from "appwrite";

export const appwriteconfig = {
  projectId: import.meta.env.VITE_APPWRITE_PROJECT_ID,
  url: import.meta.env.VITE_APPWRITE_URL,
};

export const client = new Client();

client.setProject(appwriteconfig.projectId);
client.setEndpoint(appwriteconfig.url);

export const account = new Account(client);
export const databases = new Databases(client);
export const storage = new Storage(client);
export const avatars = new Avatars(client);
```

src > types > index.ts
```
export type INavLink = {
  imgURL: string;
  route: string;
  label: string;
};

export type IUpdateUser = {
  userId: string;
  name: string;
  bio: string;
  imageId: string;
  imageUrl: URL | string;
  file: File[];
};

export type INewPost = {
  userId: string;
  caption: string;
  file: File[];
  location?: string;
  tags?: string;
};

export type IUpdatePost = {
  postId: string;
  caption: string;
  imageId: string;
  imageUrl: URL;
  file: File[];
  location?: string;
  tags?: string;
};

export type IUser = {
  id: string;
  name: string;
  username: string;
  email: string;
  imageUrl: string;
  bio: string;
};

export type INewUser = {
  name: string;
  email: string;
  username: string;
  password: string;
};
```

src > lib > appwrite > api.ts
```
import { ID } from "appwrite";
import type { INewUser } from "@/types";
import { account } from "./config";

export async function createUserAccount(user: INewUser) {
  try {
    const newAccount = await account.create(
      ID.unique(),
      user.email,
      user.password,
      user.name
    );
    return newAccount;
  } catch (error) {
    console.log(error);
    return error;
  }
}
```

### src > _auth > forms > SigninForm.tsx  

- _root

### src > _root > Rootlayout.tsx  
### src > _root > pages > Home.tsx  
### src > _root > pages > index.ts
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
