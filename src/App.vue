<template>
  <login v-if="loginIsActive" @UserInfo="pushList" @logIn="checkLoginStatus" />
  <div class="container">
    <div
      class="chat--app--container d-flex justify-content-between align-items-start"
    >
      <!-- chatsection -->
      <!-- active users -->
    </div>
    <p>{{ loginIsActive }}</p>
  </div>
</template>

<script>
import Login from "./components/login.vue";
export default {
  data() {
    return {
      loginIsActive: true,
      userInfo: [],
    };
  },
  components: {
    Login,
  },
  methods: {
    checkLoginStatus(event) {
      this.loginIsActive = event;
    },
    pushList(userList) {
      this.userInfo.push(userList);
    },
  },
};
</script>

<style>
</style>