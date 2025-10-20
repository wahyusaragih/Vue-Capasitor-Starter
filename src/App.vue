<template>
  <v-app>
    <v-main class="fullscreen">
      <v-container fluid class="d-flex align-center justify-center fill-height">
        <v-card class="pa-6 text-center" elevation="4" max-width="400">
          <v-card-title class="text-h5">👋 Hello, Vue 3 + Vuetify + Vite!</v-card-title>
          <v-card-text>
            <v-text-field v-model="name" label="Enter your name" />
            <v-btn color="primary" @click="sayHello" block>Say Hello</v-btn>

            <v-alert
              v-if="message"
              type="success"
              class="mt-4"
            >
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
  overflow: hidden; /* ✅ Prevent scrolling */
}

.fullscreen {
  height: 100vh; /* ✅ Force full viewport height */
  width: 100vw;  /* ✅ Force full viewport width */
  padding: 0 !important;
  margin: 0 !important;
}
</style>
