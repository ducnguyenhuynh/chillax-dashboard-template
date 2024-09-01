<script setup>
import { ref, onMounted } from 'vue'

import chevron  from './icons/chevron.vue';
import chart from './icons/chart.vue';
import home from './icons/home.vue';
import apartment from './icons/apartment.vue';
import camera from './icons/camera.vue';
import users from './icons/users.vue';
import docs from './icons/docs.vue';
import setting from './icons/setting.vue'
import rightArrow from './icons/rightArrow.vue'
import chat from './icons/chat.vue'
import logout from './icons/logout.vue'

const emit = defineEmits(['is_menu_expanded', 'item_chosen', 'logout_clicked'])
const menu_expanded = ref(false)
const item_chosen = ref('Home')
const menuItems = ref([
    { name: 'Home', link: '/', icon: home, hierarchy: false},
    { name: 'Chart', link: '/chart', icon: chart, hierarchy: false},
    { name: 'Apartment', link: '/apartment', icon: apartment, hierarchy: false},
    { name: 'Camera', link: '/camera', icon: camera, hierarchy: false},
    { name: 'User', link: '/user', icon: users, hierarchy: false},
    { name: 'Contract', link: '/contract', icon: docs, hierarchy: false},
    { name: 'Message', link: '/message', icon: chat, hierarchy: false},
])
// menuItems which include elements backend returned
const props = defineProps({
    items_allowed: {
        type: Array,
        required: true,
    }
})

function toggle () {
    menu_expanded.value = !menu_expanded.value
    emit('is_menu_expanded', menu_expanded.value)
}

function toggle_menu (name) {
    item_chosen.value = name
    emit('item_chosen', item_chosen.value)
}

function logout_clicked () {
    emit('logout_clicked', true)
}

</script>
<template>
    <div v-if="!menu_expanded">
        <button @click="toggle" class="transform transition duration-500 ease-in-out hover:scale-110 mt-4 mx-2 bnt ">
            <chevron></chevron>
        </button>
    </div>

    <div v-if="menu_expanded">
        <div class="fixed ml-2 mx-1 shadow-2xl h-screen flex-row w-36 bg-gray-50 rounded-lg items-center justify-center border-y-4 border-gradient-br-blue-green-gray-900 border-transparent">
            <div class="space-y-1 p-4 justify-center items-center grid grid-flow-row pr-6 mx-6 pb-6 border-b-2">
                <button @click="toggle()" class="transform transition duration-500 ease-in-out hover:scale-125 bnt">
                    <chevron class="transform rotate-180" ></chevron>
                </button>
                <img src="@/assets/logo.png" class=" w-28 mb-2"/>
            </div>
            <div class="space-y-6 pt-6 font-sans mb-10">
                <div v-for="item of menuItems" class="w-full">
                    <button @click="toggle_menu(item.name)" v-if="item.name == item_chosen" class="w-4/5 mx-4 p-2 transform transition duration-500 ease-in-out hover:scale-110 justify-start font-sans rounded-lg hover:border-y-2 hover:border-gradient-tl-blue-green-gray-900 border-transparent bg-gradient-to-br from-sky-300 to-green-300">
                        <div class="text-gray-600">
                            <component :is="item.icon"></component>
                            <div class="text-left my-2">{{ item.name }}</div>
                        </div>
                    </button>
                    <button @click="toggle_menu(item.name)" v-else class="w-4/5 ml-4 p-2 transform transition duration-500 ease-in-out hover:scale-110 justify-start font-sans rounded-lg hover:border-y-2 hover:border-gradient-tl-blue-green-gray-900 border-transparent">
                        <div class="text-gray-600">
                            <component :is="item.icon"></component>
                            <div class="text-left my-2">{{ item.name }}</div>
                        </div>
                    </button>
                </div>
            </div>
            <div class="flex justify-center">
                <div class="flex justify-center border-t-2 pt-5 w-2/3">
                    <button @click="logout_clicked()" class="transform p-2 opacity-70 rounded-lg hover:scale-125 bg-gradient-to-br hover:from-rose-500 hover:to-orange-400 hover:">
                        <logout></logout>
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.bnt {
    @apply transform transition duration-500 ease-in-out hover:scale-110 justify-center bg-gradient-to-br hover:from-sky-300 hover:to-green-300 focus:ring-2 focus:outline-none font-sans rounded-lg text-sm px-3 py-2.5 text-center inline-flex items-center me-2 mb-1;    
}
.rounded-lg {
    border-radius: 0.7rem;    
}
.border-gradient-br-blue-green-gray-900 {
  background: linear-gradient(to right, #ffffff, #ffffff),
    linear-gradient(to bottom right, #A2D5AB, #39EAE9);
  background-clip: padding-box, border-box;
  background-origin: padding-box, border-box;
}
.hover\:border-gradient-tl-blue-green-gray-900:hover {
  background: linear-gradient(to right, #ffffff, #ffffff),
    linear-gradient(to bottom right, #A2D5AB, #39EAE9);
  background-clip: padding-box, border-box;
  background-origin: padding-box, border-box;
}
</style>