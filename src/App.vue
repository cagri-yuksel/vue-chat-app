<template>
  <login v-if="true" />
  <div class="container">
    <div
      class="chat--app--container d-flex justify-content-between align-items-start"
    >
      <!-- chatsection -->
      <!-- active users -->
    </div>
  </div>
</template>

<script>
import Login from "./components/login.vue";
import axios from "axios"
export default {
  components: {
    Login,
  },
  created() {
     axios
      .get("http://localhost:3000/user")
      .then((response) => {
        console.log("response", response);
        // this.comments = response.data.filter((c) => c.id <= 10);
      })
      .catch((e) => {
        console.log("e", e);
      });
  },
};
</script>

<style>
</style>