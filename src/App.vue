<template>
      <login v-if="true" />
  <div class="container">
    <div class="chat--app--container d-flex justify-content-between align-items-start">
      <!-- chatsection -->
      <!-- active users -->
    </div>
  </div>
</template>

<script>
import Login from "./components/login.vue";
export default {
  components: {
    Login,
  },
  methods: {
    checkLoginStatus(status) {
     this.loginIsActive = this.status;
    },
    pushList(userList) {
      this.userInfo.push(userList);
    },
  },
};
</script>

<style>
</style>