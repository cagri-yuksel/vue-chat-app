<template>
<div>
  <ul><li v-for="i in userInfo" :key="i.id"> aktif kullanıcı kim?  {{i.username}} </li></ul>
  <login v-if="loginIsActive" @UserInfo="pushList" @logIn="checkLoginStatus" />

  <div class="container">
    <div
      class="chat--app--container d-flex justify-content-between align-items-start"
    >
      <chat-section
        v-if="!loginIsActive"
        :users="users"
        @send-message-event="sendMessage"
        :activeUser="activeUser"
      />
      <active-users :userInfo="userInfo" v-if="!loginIsActive" />
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
      loginIsActive: true,
      userInfo: [],
    };
  },
  /*   created() {
    axios
      .get("http://localhost:3000/users")
      .then((response) => {
        console.log("response", response);
        // this.comments = response.data.filter((c) => c.id <= 10);
      })
      .catch((e) => {
        console.log("e", e);
      });
  }, */
  methods: {
    sendMessage(value) {
      if (value != "") {
        this.userData.message = value;
        this.users.push({ ...this.userData });
        console.log(this.users);
      }
    },
    checkLoginStatus(event) {
      this.loginIsActive = event;
    },
    pushList(userList) {
      this.userInfo = userList;
    },
  },
};
</script>

