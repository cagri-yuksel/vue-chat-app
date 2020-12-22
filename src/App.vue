<template>
  <div>
    <login
      v-if="loginIsActive"
      @UserInfo="pushList"
      @logIn="checkLoginStatus"
    />

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
        <active-users  @toUserChange="changeUser" v-if="!loginIsActive" />
        <!-- chatsection -->
        <!-- active users -->
        <!-- database yeniden topluyalım [[ ]] olarak dönüyor o bende çalışanı koydum -->
        <!-- login tamam hızlıca tasarımı bitiririm. -->
        <!-- chatting bence ayrı olmalı chat ayrı bir arrayi içinde app.vue içersinde aktif kullanıcın id si yada nicki alınarak chat
      arrayi içersinden ona ait olan konuşmalar dökülsün  -->
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
     changeToUser:null,
    };
  },
  methods: {
    checkLoginStatus(event) {
      this.loginIsActive = event;
    },
    pushList(userList) {
      this.userInfo.push(...userList);
    },
    changeUser(toUser){
      this.changeToUser = toUser
      console.log("app vue", this.changeToUser.id)

    }
  },
};
</script>

