<template>
  <div class="card mr-10">
    <ul class="messages" ref="container">
      <li
        v-for="user in users"
        :key="user.id"
        :class="{ 'current-user': activeUser }"
      >
        {{ user.message }}<small>14:55</small>
      </li>
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
export default {
  props: ["users", "activeUser"],
  data() {
    return {
      message: "",
    };
  },

  methods: {
    scrollToEnd() {
      let content = this.$refs.container;
      content.scrollTop = content.scrollHeight;
    },

    testMethod() {
    
      this.$emit("send-message-event", this.message);
      this.message = "";
      console.log("mesaj", this.message);
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
};
</script>

