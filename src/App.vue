<template>
  <login
    @UserInfo="pushList"
    @loggedIn="checkLoginStatus"
    v-if="loginIsActive"
  />
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