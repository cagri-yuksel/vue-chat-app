<template>
  <!-- <login v-if="true" /> -->
  <div class="container">
    <div
      class="chat--app--container d-flex justify-content-between align-items-start"
    >
      <chat-section
        :users="users"
        @send-message-event="sendMessage"
        :activeUser="activeUser"
      />
      <active-users />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import chatSection from "./components/chatSection.vue";
import activeUsers from "./components/activeUsers.vue";

/* import Login from "./components/login.vue"; */
export default {
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
};
</script>

