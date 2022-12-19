<script setup lang="ts">
import MainView from "./views/MainView.vue";
import LoginVIew from "./views/LoginView.vue";
import { onMounted } from "vue";
import { useLoginStore } from "@/stores/login";
const loginStore = useLoginStore();
onMounted(() => {
  console.log("On Mounted");
  loginStore.loadData();
});
</script>

<template>
  <LoginVIew v-if="!loginStore.loginName" @login="loginStore.login" />
  <MainView
    v-if="loginStore.isLogin"
    @logout="loginStore.logout"
    :loginName="loginStore.loginName"
  />
</template>

<style scoped></style>
