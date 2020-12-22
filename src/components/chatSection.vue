<template>
  <div class="card mr-10">
    <ul class="messages " ref="container">
      <li :class="{ 'current-user' : userInfo[0].id == i.id }" v-for="i in chatLog"  :key="i">{{ i.mesaj }}</li>
    </ul>
    <div class="text-container d-flex justify-content-start align-items-start">
      <input @keypress.enter="testMethod" v-model="message" type="text" />
      <button :disabled="isDisable" class="btn-primary" @click="testMethod()">
        Send
      </button>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  props: [ "userInfo", "changeToUser"],
  data() {
    return {
      chatLog: [],
      message: {},
    };
  },

  methods: {
    scrollToEnd() {
      let content = this.$refs.container;
      content.scrollTop = content.scrollHeight;
    },
  },
  computed: {
    isDisable() {
      return this.message == "" ? true : false;
    },
  },

  updated() {
    this.scrollToEnd();
  },
  mounted() {
    this.scrollToEnd();
  },
  watch:{
    changeToUser(n){
      axios
        .get(
          "http://localhost:3000/chat?id="+this.userInfo[0].id+"&to="+this.changeToUser.id+"&to="+this.userInfo[0].id+"&id="+this.changeToUser.id
        )
        .then((response) => {
          console.log("response chat", response);
          this.chatLog = []
          this.chatLog.push(...response.data);
        })
        .catch((e) => {
          console.log("e", e);
        });
    }
  }
};
</script>
<style scoped>
.back {
  background-color: #edafb8 !important;
}
</style>
