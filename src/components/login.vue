<template>
  <div class="container position-relative">
    <div>
      <input type="text" v-model="username" />
      <input type="password" v-model="pswrd" />
      <button @click="checkLogin" class="btn btn-waring">Giriş yap</button>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      username: null,
      pswrd: null,
      userList: null,
      status: true,
    };
  },
  /// 
  methods: {
    checkLogin() {
      axios
        .get("http://localhost:3000/users?password="+this.pswrd+"&username="+this.username)
        .then((res) => {
          this.userList = res.data;
          console.log(res);
          if (this.userList.length > 0) {
            this.status = false;
            this.$emit("logIn", this.status);
            this.$emit("UserInfo", this.userList);
          } else {
            this.status = true;
          }
        })
        .catch((e) => {
          console.log("e", e);
        });
    },
  },
};
</script>
<style>
</style>