# 🚀 Vue 3 + Vuetify 3 + Vite + Capacitor Starter

![Vue](https://img.shields.io/badge/Vue-3.5.x-brightgreen)
![Vuetify](https://img.shields.io/badge/Vuetify-3.10.x-blue)
![Vite](https://img.shields.io/badge/Vite-5.x-yellow)
![Capacitor](https://img.shields.io/badge/Capacitor-7.x-purple)
![License](https://img.shields.io/badge/license-MIT-green)

A **ready-to-use starter template** for building modern **Vue 3 + Vuetify 3** apps powered by **Vite**, with **Capacitor** support for Android deployment.  
Perfect for developers who want fast builds, responsive UI, and smooth Android integration.

---

## 📚 Table of Contents

- [Project Setup](#-project-setup)
- [Install Vuetify](#-install-vuetify)
- [Setup Router](#-setup-router)
- [Create Landing Page](#-create-landing-page)
- [Configure Vuetify](#-configure-vuetify)
- [Setup Vuetify Plugin](#-setup-vuetify-plugin)
- [Run the App](#-run-the-app)
- [Node.js Version Fix (Optional)](#-nodejs-version-fix-optional)
- [Add Capacitor for Android](#-add-capacitor-for-android)
- [Build APK](#-build-apk)
- [Push to GitHub](#-push-to-github)

---

## 🧱 Project Setup

Create a new Vue 3 project with **Vite**:

```bash
npm create vite@latest new-app-test
```

When prompted:

- **Framework:** Vue  
- **Variant:** JavaScript (or TypeScript)  
- **Install dependencies now?** No

Then move into the project:

```bash
cd new-app-test
```

---

## 🎨 Install Vuetify

Install Vuetify and required dependencies:

```bash
npm install vuetify@latest
npm install -D sass sass-loader vite-plugin-vuetify
npm install @mdi/font
npm install vue-router
```

---

## 🧭 Setup Router

Create `src/router/index.js`:

```js
import { createRouter, createWebHistory } from 'vue-router'
import LandingPage from '@/views/LandingPage.vue'

const routes = [
  { path: '/', name: 'Home', component: LandingPage },
]

export default createRouter({
  history: createWebHistory(),
  routes,
})
```

---

## 🏠 Create Landing Page

Create `src/views/LandingPage.vue`:

```vue
<template>
  <v-app>
    <v-main class="fullscreen">
      <v-container fluid class="d-flex align-center justify-center fill-height">
        <v-card class="pa-6 text-center" elevation="4" max-width="400">
          <v-card-title class="text-h5">👋 Hello, Vue 3 + Vuetify + Vite!</v-card-title>
          <v-card-text>
            <v-text-field v-model="name" label="Enter your name" />
            <v-btn color="primary" @click="sayHello" block>Say Hello</v-btn>

            <v-alert v-if="message" type="success" class="mt-4">
              {{ message }}
            </v-alert>
          </v-card-text>
        </v-card>
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
import { ref } from 'vue'

const name = ref('')
const message = ref('')

const sayHello = () => {
  message.value = `Hello, ${name.value || 'Stranger'}! 👋`
}
</script>

<style>
html, body, #app {
  height: 100%;
  margin: 0;
  overflow: hidden;
}

.fullscreen {
  height: 100vh;
  width: 100vw;
  padding: 0 !important;
  margin: 0 !important;
}
</style>
```

---

## ⚙️ Configure Vuetify in `vite.config.js`

```js
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'
import vuetify from 'vite-plugin-vuetify'
import path from 'path'

export default defineConfig({
  plugins: [vue(), vuetify({ autoImport: true })],
  resolve: {
    alias: {
      '@': path.resolve(__dirname, 'src'),
    },
  },
})
```

---

## 🧩 Setup Vuetify Plugin

Create `src/plugins/vuetify.js`:

```js
import 'vuetify/styles'
import { createVuetify } from 'vuetify'
import * as components from 'vuetify/components'
import * as directives from 'vuetify/directives'

export default createVuetify({
  components,
  directives,
})
```

Update `src/main.js`:

```js
import { createApp } from 'vue'
import App from './App.vue'
import router from './router'
import { createVuetify } from 'vuetify'
import 'vuetify/styles'
import '@mdi/font/css/materialdesignicons.css'

const vuetify = createVuetify({
  theme: {
    defaultTheme: 'light',
  },
})

createApp(App)
  .use(router)
  .use(vuetify)
  .mount('#app')
```

---

## 🧠 Create Simple UI

`src/App.vue`:

```vue
<template>
  <v-app class="mt-12 pb-12">
    <router-view />
  </v-app>
</template>

<script setup>
// Empty — Vuetify and Router are initialized in main.js
</script>

<style>
html, body, #app {
  height: 100%;
  margin: 0;
  background-color: #f5f5f5;
}
</style>
```

---

## 🚀 Run the App

```bash
npm install
npm run dev
```

---

## 🩹 Node.js Version Fix (Optional)

Ensure Node.js ≥ 20.19:

```bash
sudo apt-get update
sudo apt-get install -y nodejs npm

# Install nvm if needed
curl -fsSL https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
source ~/.bashrc

# Install a supported Node version
nvm install 22
nvm use 22
node -v
npm run dev
```

---

## 📱 Add Capacitor for Android

```bash
npm install @capacitor/core
npm install --save-dev @capacitor/cli
npx cap init
```

- **Name:** NewAppTest  
- **Package ID:** com.ginko.app

Add Android platform:

```bash
npm install @capacitor/android
npx cap add android
npm run build
npx cap sync android
npx cap open android
```

---

## 🧩 Build APK

- Open **Android Studio** with the `android/` folder  
- Select **Build → Generate Signed Bundle / APK**  
- Configure keystore if needed  
- Build debug or release APK  

APK locations:

- Debug: `android/app/build/outputs/apk/debug/app-debug.apk`  
- Release: `android/app/build/outputs/apk/release/app-release.apk`  

> ⚠️ `flatDir` warnings are safe to ignore unless build errors occur.

---

## 🧠 Push to GitHub

```bash
git init
git add .
git commit -m "Initial commit"
```

Create a new repository on [GitHub](https://github.com/new) and connect it:

```bash
git remote add origin https://github.com/USERNAME/vue-vuetify-app.git
git branch -M main
git push -u origin main
```

### PowerShell Shortcut

```bash
npm run build; git add .; git status; git commit -m "Initial commit"; git push -u origin main
```

---

✅ **Your project is now ready for web and Android deployment!**
