<script setup>
import { useRoute, useRouter } from "vue-router";
import { data, fn } from "../../data.js";
import { ref, watch } from "vue";

const route = useRoute();
const router = useRouter();

const name = ref("");
const email = ref("");
const password = ref("");

const registerUser = () => {
  const res = fn.fetchPublicApi(
    "/api/register",
    { name: name.value, email: email.value, password: password.value },
    "POST"
  );
  res.then((response) => {
    router.push("/login");
  });
};
</script>
<template>
  <div class="w-full">
    <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
      <div class="mb-4">
        <label class="block text-gray-700 text-sm font-bold mb-2" for="name">
          Name
        </label>
        <input
          v-model="name"
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          id="name"
          type="text"
          placeholder="name"
        />
      </div>
      <div class="mb-4">
        <label class="block text-gray-700 text-sm font-bold mb-2" for="email">
          Email
        </label>
        <input
          v-model="email"
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          id="email"
          type="email"
          placeholder="email"
        />
      </div>
      <div class="mb-6">
        <label
          class="block text-gray-700 text-sm font-bold mb-2"
          for="password"
        >
          Password
        </label>
        <input
          v-model="password"
          class="shadow appearance-none borde rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline"
          id="password"
          type="password"
          placeholder="******************"
        />
      </div>
      <div class="flex items-center justify-between">
        <button
          @click="registerUser()"
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
          type="button"
        >
          Sign Up
        </button>
        <router-link to="/login">Sign In</router-link>
      </div>
    </form>
  </div>
</template>