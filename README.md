# Vue 3 + Vuetify 3 + Vite + Capacitor Starter

![Vue](https://img.shields.io/badge/Vue-3.3.0-brightgreen)
![Vuetify](https://img.shields.io/badge/Vuetify-3.3.0-blue)
![Vite](https://img.shields.io/badge/Vite-4.4.0-yellow)
![Capacitor](https://img.shields.io/badge/Capacitor-5.0.0-purple)

A starter template for building a **Vue 3** project with **Vuetify 3**, **Vite**, and **Capacitor** for Android deployment.

---

## Table of Contents

* [Project Setup](#project-setup)
* [Install Vuetify](#install-vuetify)
* [Configure Vuetify](#configure-vuetify)
* [Setup Vuetify Plugin](#setup-vuetify-plugin)
* [Create Simple UI](#create-simple-ui)
* [Run the App](#run-the-app)
* [Node.js Version Fix](#nodejs-version-fix-optional)
* [Add Capacitor](#add-capacitor-for-android)
* [Build APK](#build-apk)
* [Push to GitHub](#push-to-github)

---

## 🧱 Project Setup

Create a new Vue 3 project with Vite:

```bash
npm create vite@latest new-app-test
```

When prompted:

* **Framework:** Vue
* **Variant:** JavaScript (or TypeScript)
* **Install dependencies now?** No

Move into your project:

```bash
cd new-app-test
```

---

## 🎨 Install Vuetify 3

```bash
npm install vuetify@latest
npm install -D sass sass-loader vite-plugin-vuetify
```

---

## ⚙️ Configure Vuetify in `vite.config.js`

```javascript
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'
import vuetify from 'vite-plugin-vuetify'

export default defineConfig({
  plugins: [
    vue(),
    vuetify({ autoImport: true }),
  ],
})
```

---

## 🧩 Setup Vuetify Plugin

Create `src/plugins/vuetify.js`:

```javascript
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

```javascript
import { createApp } from 'vue'
import App from './App.vue'
import './style.css'
import vuetify from './plugins/vuetify'

createApp(App).use(vuetify).mount('#app')
```

---

## 🧠 Create Simple UI

`src/App.vue`:

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
  overflow: hidden; /* Prevent scrolling */
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

## 🧩 Add Capacitor for Android

```bash
npm install @capacitor/core
npm install --save-dev @capacitor/cli
npx cap init
```

* **Name:** NewAppTest
* **Package ID:** com.ginko.app

Add Android platform:

```bash
npm install @capacitor/android
npx cap add android
npm run build
npx cap sync android
npx cap open android
```

---

## 📱 Build APK

* Open **Android Studio** with `android/` folder
* Select **Build → Generate Signed Bundle / APK**
* Configure keystore if needed
* Build debug or release APK

APK locations:

* Debug: `android/app/build/outputs/apk/debug/app-debug.apk`
* Release: `android/app/build/outputs/apk/release/app-release.apk`

> ⚠️ `flatDir` warning is safe to ignore unless build errors occur.

---

## 🧩 Push to GitHub

```bash
git init
git add .
git commit -m "Initial commit"
```

* Create a new repository on [GitHub](https://github.com/new)
* Connect your local repo:

```bash
git remote add origin https://github.com/USERNAME/vue-vuetify-app.git
git branch -M main
git push -u origin main
```
#### PowerShell Shortcut

PowerShell

```sh
npm run build; git add .; git status; git commit -m "Initial commit"; git push -u origin main
```
---

✅ Your project is now ready for **web and Android deployment**!
