<script setup lang="ts">
import MainView from "./views/MainView.vue";
import LoginVIew from "./views/LoginView.vue";
import { computed, ref } from "vue";
const loginName = ref("");
const isLogin = computed(() => {
  //loginName is not empty
  return loginName.value !== "";
});
const login = (userName: string): void => {
  loginName.value = userName;
};
const logout = () => {
  loginName.value = "";
};
</script>

<template>
  <LoginVIew v-if="!loginName" @login="login" />
  <MainView v-if="isLogin" @logout="logout" />
</template>

<style scoped></style>
