<script setup>
import { ref } from 'vue'
import { RouterLink, RouterView} from 'vue-router'
import LoginView from './views/LoginView.vue'
import HomeView from './views/HomeView.vue'
const isUser = ref(false)

function check_user_status(payload) {
  isUser.value = payload
  console.log(isUser.value);
}

</script>
<template>
  <body>
    <login-view @loginEmit="check_user_status" v-if="!isUser"></login-view>
    <home-view v-if="isUser" @logoutEmit="check_user_status"></home-view>
  </body>
</template>
<style scoped>
</style>
