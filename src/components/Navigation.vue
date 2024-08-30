<script setup>
import { ref } from 'vue'
import chevron  from './icons/chevron.vue';
const expanded = ref(false)

function toggle () {
    expanded.value = !expanded.value
}
</script>
<template>
    <aside class="h-screen rounded-lg shadow-md bg-teal-100 " :class="{'w-28': expanded, 'w-14': !expanded }">
        <nav class="h-full flex-col"  >
            <div class="p-4 pb-2 justify-between items-center" >
                <img src="../assets/logo.png" class="overflow-hidden flex"/>
                <button @click="toggle"  class="rotate-180">
                    <chevron class="rounded-lg bg-rose-100 hover:bg-teal-300" />
                </button>
            </div>

            <!-- <SidebarContext.Provider value={{ expanded }}>

                <ul className="flex-1 px-3">{children}</ul>
            </SidebarContext.Provider>

            <div className="border-t flex p-3">
                <img src={profile} className="w-10 h-10 rounded-md" />
                <div className={`flex justify-between items-center overflow-hidden transition-all ${expanded ? "w-52 ml-3" : "w-0"} `}>
                    <div className="leading-4">
                        <h4 className="font-semibold">constGenius</h4>
                        <span className="text-xs text-gray-600">constgenius@gmail.com</span>
                    </div>
                    <MoreVertical size={20} />
                </div>
            </div> -->
        </nav>
    </aside>
</template>