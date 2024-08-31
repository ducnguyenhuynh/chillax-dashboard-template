<script setup>
import { ref } from 'vue'
import { RouterLink, RouterView} from 'vue-router'
import Login from './views/Login.vue'
import HomeView from './views/HomeView.vue'
import isUser from './views/Login.vue' 

</script>

<template>
  <body>
    <!-- <Login v-if="!isUser.value" v-on="isUser"></Login> -->
    <HomeView></HomeView>
  </body>
</template>

<style scoped>

</style>
