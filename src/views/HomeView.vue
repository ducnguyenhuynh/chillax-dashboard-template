<script setup>
import { ref } from 'vue'
import Navigation from '@/components/Navigation.vue';
import News from '@/components/News.vue'
import Charts from '@/components/Charts.vue'
import Messages from '@/components/Messages.vue'
import Apartments from '@/components/Apartments.vue'
import Users from '@/components/Users.vue';
import Camera from '@/components/Camera.vue';
import Payment from '@/components/payment.vue';

const menu_expanded = ref(false)
const page_chosen = ref('Home')
const logout_signal = ref(false)
const items_allowed = ref(['Home', 'Chart', 'Apartment', 'Camera', 'User', 'Contract', 'Message'])

const emits = defineEmits(['logoutEmit'])
function handleMenuExpandedEvent(payload) {
    menu_expanded.value = payload;
}
function handlePageChosenEvent(payload) {
    page_chosen.value = payload
}
function handleLogoutEvent(payload) {
    logout_signal.value = payload
    emits('logoutEmit', false)
}
</script>
<template>
    <div id="menu">
        <Navigation @is_menu_expanded="handleMenuExpandedEvent" @item_chosen="handlePageChosenEvent" @logout_clicked="handleLogoutEvent" :items_allowed="items_allowed">

        </Navigation>
    </div>
    <div class="flex flex-row">
        <div v-if="menu_expanded" class="w-40"></div>
        <!-- <div> {{ page_chosen }}</div> -->
        <News v-if="page_chosen === 'Home'"></News>
        <Charts v-else-if="page_chosen === 'Chart'" class="m-5"></Charts>
        <Messages v-else-if="page_chosen === 'Message'"></Messages>
        <Apartments v-else-if="page_chosen === 'Apartment'"></Apartments>
        <Users v-else-if="page_chosen === 'User'"></Users>
        <Camera v-else-if="page_chosen === 'Camera'"></Camera>
        <Payment v-else-if="page_chosen === 'Contract'"></Payment>
    </div>
</template>
