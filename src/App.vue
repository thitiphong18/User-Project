<script setup lang="ts">
import MainView from "./views/MainView.vue";
import LoginVIew from "./views/LoginView.vue";
import { ref } from "vue";
const loginName = ref("");
const isLogin = computed(() => {
  //loginName is not empty
  return loginName.value !== "";
});
</script>

<template>
  <LoginVIew v-if="!loginName" />
  <MainView v-if="isLogin" />
</template>

<style scoped></style>
