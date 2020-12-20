<template>
 baris
  <!-- <login v-if="true" /> -->

  <login v-if="loginIsActive" @UserInfo="pushList" @logIn="checkLoginStatus" />
 test
  <div class="container">
    <div
      class="chat--app--container d-flex justify-content-between align-items-start"
    >
     baris
      <chat-section
        :users="users"
        @send-message-event="sendMessage"
        :activeUser="activeUser"
      />
      <active-users />

      <!-- chatsection -->
      <!-- active users -->
 test
    </div>
    <p>{{ loginIsActive }}</p>
  </div>
</template>

<script>
import axios from "axios";
import chatSection from "./components/chatSection.vue";
import activeUsers from "./components/activeUsers.vue";

/* import Login from "./components/login.vue"; */
export default {
  data() {
    return {
      loginIsActive: true,
      userInfo: [],
    };
  },
  components: {
    chatSection,
    activeUsers,
    /*     Login, */
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
      activeUser: true,
    };
  },
  created() {
    axios
      .get("http://localhost:3333/user")
      .then((response) => {
        console.log("response", response);
        // this.comments = response.data.filter((c) => c.id <= 10);
      })
      .catch((e) => {
        console.log("e", e);
      });
  },
  methods: {
    sendMessage(value) {
      if (value != "") {
        this.userData.message = value;
        this.users.push({ ...this.userData });
        console.log(this.users);
      }
    },
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

