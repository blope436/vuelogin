<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";
import useAuth from "../composable/useAuth";


const { isAuthenticated, login } = useAuth();

const username = ref("");
const password = ref("");

const router = useRouter();


import { useTimeout, promiseTimeout } from "@vueuse/core";

</script>

<template>
<div class="flex items-center justify-center text-yellow-800 text-5xl text-center bg-purple-200">
<img class="w-40" src="/src/assets/login.png" alt="Login Image"/>
<h1>Login Form </h1>
</div>
<div class="flex flex-col justify-center text-center py-20 min-h-screen-nonav">
    <img class=" w-40 h-40 shadow-lg" src="/src/assets/password.png" alt="Login Image"/>
    <form @submit.prevent="login(username,password)" class=" bg-indigo-300 flex flex-col space-y-10">
        <input type="text" class="rounded-lg border-2" placeholder="Username" v-model="username"/>
        <input type="password" class="rounded-lg border-2 " placeholder="Password" v-model="password"/>
        <button type="submit" @submit.prevent="login(username,password)" class="rounded-lg bg-blue-600 text-blue-200">Login</button>
    </form>
</div>
<div class="absolute w-1/3 bg-red-500 text-xl bottom-2 right-2 rounded-lg p-4 text-center text-pink-200">
    Logged In: {{isAuthenticated}}
</div>

</template>