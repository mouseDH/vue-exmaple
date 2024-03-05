<template>
    <!-- Use defineAsyncComponent  -->
    <button @click="show = true">Login</button>
    <login-popup v-if="show" />
  </template>
  
  <script>
  import { defineAsyncComponent } from 'vue'
  export default {
    components: {
      LoginPopup: defineAsyncComponent(() =>
        import('./components/LoginPopup.vue')
        // import("http://devcrate.local/product/components/Subcomponent.vue")
      ),
    },
    data() {
      return {
        show: false,
      }
    },
  }
  </script>
  