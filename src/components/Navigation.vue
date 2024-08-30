<script setup>
import { ref } from 'vue'
import chevron  from './icons/chevron.vue';
import chart from './icons/chart.vue';
import home from './icons/home.vue';
import apartment from './icons/apartment.vue';
import camera from './icons/camera.vue';
import users from './icons/users.vue';
import docs from './icons/docs.vue';
const expanded = ref(true)

const menuItems = ref([
        { name: 'Home', link: '/', icon: home},
        { name: 'Chart', link: '/chart', icon: chart},
        { name: 'Apartment', link: '/apartment', icon: apartment},
        { name: 'Camera', link: '/camera', icon: camera},
        { name: 'User', link: '/user', icon: users},
        { name: 'Contract', link: '/contract', icon: docs},
      ])

function toggle () {
    expanded.value = !expanded.value
}

</script>
<template>
    <div v-if="!expanded">
        <button @click="toggle" class="transform transition duration-500 ease-in-out hover:scale-110 mt-4 mx-2 bnt ">
            <chevron></chevron>
        </button>
    </div>

    <div v-if="expanded">
        <div class="h-screen w-48 bg-white rounded-lg items-center justify-center shadow-md border-r-2 border-gradient-br-blue-green-gray-900 border-transparent">
            <div class="space-y-1 p-4 justify-center items-center grid grid-flow-row">
                <button @click="toggle" class="transform transition duration-500 ease-in-out hover:scale-125 justify-center px-3 py-2.5 text-center inline-flex items-center me-2 mb-1">
                    <chevron></chevron>
                </button>
                <img src="@/assets/logo.png" class="w-16 mr-2"/>
            </div>
            <div class="space-y-6 pt-6 font-sans">
                <div v-for="item of menuItems" class="w-40">
                    <button class="ml-4 p-2 transform transition duration-500 ease-in-out hover:scale-110 justify-center text-left font-sans w-full rounded-lg hover:border-y-2 hover:border-gradient-tl-blue-green-gray-900 border-transparent">
                        <div class="grid grid-flow-col text-gray-600 ">
                            <component :is="item.icon"></component>
                            {{ item.name }}
                        </div>
                    </button>
                </div>
            </div>
            <div class="space-y-6 pt-6 font-semibold">
                <div>

                </div>
            </div>
        </div>
        
    </div>
</template>

<style scoped>
.bnt {
    @apply transform transition duration-500 ease-in-out hover:scale-110 justify-center bg-gradient-to-br hover:from-sky-300 hover:to-green-300 focus:ring-2 focus:outline-none font-semibold rounded-lg text-sm px-3 py-2.5 text-center inline-flex items-center me-2 mb-1;    
}
.border-gradient-br-blue-green-gray-900 {
  background: linear-gradient(to right, #ffffff, #ffffff),
    linear-gradient(to bottom right, #60A5FA, #4ADE80);
  background-clip: padding-box, border-box;
  background-origin: padding-box, border-box;
}
.hover\:border-gradient-tl-blue-green-gray-900:hover {
  background: linear-gradient(to right, #ffffff, #ffffff),
    linear-gradient(to bottom right, #60A5FA, #4ADE80);
  background-clip: padding-box, border-box;
  background-origin: padding-box, border-box;
}
</style>