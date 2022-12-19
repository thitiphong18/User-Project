<script setup lang="ts">
import MainView from "./views/MainView.vue";
import LoginVIew from "./views/LoginView.vue";
import { computed, onMounted, ref } from "vue";
const loginName = ref("");
const isLogin = computed(() => {
  //loginName is not empty
  return loginName.value !== "";
});
const login = (userName: string): void => {
  loginName.value = userName;
  localStorage.setItem("loginName", userName);
};
const logout = () => {
  loginName.value = "";
  localStorage.removeItem("loginName");
};
const loadData = () => {
  loginName.value = localStorage.getItem("loginName") || "";
};
onMounted(() => {
  console.log("On Mounted");
  loadData();
});
</script>

<template>
  <LoginVIew v-if="!loginName" @login="login" />
  <MainView v-if="isLogin" @logout="logout" />
</template>

<style scoped></style>
