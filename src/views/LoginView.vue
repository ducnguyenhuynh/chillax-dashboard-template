<script setup>
import { ref } from 'vue'
const email = ref('')
const password = ref('')
const isUser = ref(false)

const emit = defineEmits(['loginEmit'])

function login() {
    // verify password and email
    isUser.value = true
    emit('loginEmit', isUser.value)
    
}
</script>

<template>
    <body class="bg-cover h-screen bg-gradient-to-br from-sky-200 to-rose-100">
    <div class="grid grid-cols-1 gap-1">
        <div >
            <img class="mx-auto h-40 w-auto" src="@/assets/logo.png">
        </div>
        <div class="mx-0">
            <div class="flex min-h-full flex-col justify-center px-6 py-1 lg:px-8 ">
                <div class="sm:mx-auto sm:w-full sm:max-w-sm">
                    <h2 class="mt-1 text-center text-2xl font-bold leading-9 tracking-tight text-gray-900">Sign in to your account</h2>
                </div>

                <div class="mt-10 sm:mx-auto sm:w-full sm:max-w-sm">
                    <form class="space-y-6" action="#" method="POST">
                    <div>
                        <label for="email" class="block text-sm font-medium leading-6 text-gray-900">Email address</label>
                        <div class="mt-2">
                            <input v-model="email" id="email" name="email" type="email" autocomplete="email" required class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-sky-400 focus:border-sky-400 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-sky-400 dark:focus:border-sky-400" placeholder="chillax@gmail.com">
                        </div>
                    </div>

                    <div>
                        <div class="flex items-center justify-between">
                        <label for="password" class="block text-sm font-medium leading-6 text-gray-900">Password</label>
                        <div class="text-sm">
                            <a href="#" class="font-semibold text-sky-500 hover:text-teal-400">Forgot password?</a>
                        </div>
                        </div>
                        <div class="mt-2">
                            <input v-model="password" type="password" id="password" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-sky-400 focus:border-sky-400 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-sky-400 dark:focus:border-sky-400" placeholder="•••••••••" required />
                        </div>
                        
                    </div>

                    <div>
                        <button type="button" class="flex w-full justify-center rounded-md bg-sky-500 px-3 py-1.5 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-teal-400 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-sky-500"  @click="login()">Login</button>
                    </div>
                    </form>

                    <p class="mt-10 text-center text-sm text-gray-500">
                        Not a member?
                        <a href="#" class="font-semibold leading-6 text-sky-500 hover:text-teal-400">Sign In</a>
                        or
                    </p>

                    <div class="mt-5 grip grip-cols-3 grap-4 flex justify-center">
                        <button type="button" class="justify-centerh-10 w-40 bg-gradient-to-br from-sky-300 to-sky-400 text-white hover:from-teal-300 hover:to-teal-400 focus:ring-2 focus:outline-none font-semibold rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center me-2 mb-2">
                            <svg class="w-auto h-4 me-2" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 8 19">
                                <path fill-rule="evenodd" d="M6.135 3H8V0H6.135a4.147 4.147 0 0 0-4.142 4.142V6H0v3h2v9.938h3V9h2.021l.592-3H5V3.591A.6.6 0 0 1 5.592 3h.543Z" clip-rule="evenodd"/>
                            </svg>
                            Facebook
                        </button>
                        <button type="button" class="justify-center h-10 w-40 bg-gradient-to-br from-sky-400 to-rose-200 text-white hover:from-teal-300 hover:to-teal-400 focus:ring-2 focus:outline-none font-semibold rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center me-2 mb-2">    
                            
                            <svg class="w-auto h-4 me-2" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 18 19">
                                <path fill-rule="evenodd" d="M8.842 18.083a8.8 8.8 0 0 1-8.65-8.948 8.841 8.841 0 0 1 8.8-8.652h.153a8.464 8.464 0 0 1 5.7 2.257l-2.193 2.038A5.27 5.27 0 0 0 9.09 3.4a5.882 5.882 0 0 0-.2 11.76h.124a5.091 5.091 0 0 0 5.248-4.057L14.3 11H9V8h8.34c.066.543.095 1.09.088 1.636-.086 5.053-3.463 8.449-8.4 8.449l-.186-.002Z" clip-rule="evenodd"/>
                            </svg>
                            Google
                        </button>
                        <button type="button" class="justify-center h-10 w-40 bg-gradient-to-br from-rose-200 to-rose-300 text-white hover:from-teal-300 hover:to-teal-400 focus:ring-2 focus:outline-none font-semibold rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center me-2 mb-2">    
                            <svg class="w-auto h-4 me-2" aria-hidden="true" focusable="false" data-prefix="fab" data-icon="apple" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 384 512"><path fill="currentColor" d="M318.7 268.7c-.2-36.7 16.4-64.4 50-84.8-18.8-26.9-47.2-41.7-84.7-44.6-35.5-2.8-74.3 20.7-88.5 20.7-15 0-49.4-19.7-76.4-19.7C63.3 141.2 4 184.8 4 273.5q0 39.3 14.4 81.2c12.8 36.7 59 126.7 107.2 125.2 25.2-.6 43-17.9 75.8-17.9 31.8 0 48.3 17.9 76.4 17.9 48.6-.7 90.4-82.5 102.6-119.3-65.2-30.7-61.7-90-61.7-91.9zm-56.6-164.2c27.3-32.4 24.8-61.9 24-72.5-24.1 1.4-52 16.4-67.9 34.9-17.5 19.8-27.8 44.3-25.6 71.9 26.1 2 49.9-11.4 69.5-34.3z"></path></svg>
                            Apple
                        </button>
                    </div>

                </div>
                </div>
        </div>
    </div>
    </body>

</template>

<style scoped>
</style>
