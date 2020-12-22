<template>
  <div>
    <div>
      <login
        v-if="loginIsActive"
        @UserInfo="pushList"
        @logIn="checkLoginStatus"
      />
    </div>

    <div class="container">
      <div
        class="chat--app--container d-flex justify-content-between align-items-start"
      >
        <chat-section
          :userInfo="userInfo"
          v-if="!loginIsActive"
          :users="users"
          :changeToUser="changeToUser"
        />
        <active-users
          :userInfo="userInfo"
          @toUserChange="changeUser"
          v-if="!loginIsActive"
        />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import chatSection from "./components/chatSection.vue";
import activeUsers from "./components/activeUsers.vue";
import login from "./components/login";

/* import Login from "./components/login.vue"; */
export default {
  components: {
    chatSection,
    activeUsers,
    login,
  },
  data() {
    return {
      users: [],
      userData: {
        username: "baristunar",
        password: "123",
        fullName: "Barış Tunar",
        message: "",
      },
      userInfo: [],
      loginIsActive: true,
      changeToUser: null,
    };
  },
  methods: {
    checkLoginStatus(event) {
      this.loginIsActive = event;
    },
    pushList(userList) {
      this.userInfo.push(...userList);
    },
    changeUser(toUser) {
      this.changeToUser = toUser;
    },
  },
};
</script>
<style scoped>
.back {
  background-color: #edafb8 !important;
}
</style>

