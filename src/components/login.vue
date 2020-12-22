<template>
<div >
  <div class="container centered ">
    <div>
      <form class="px-4 py-3">
        <div class="mb-3">
          <label class="form-label"
            >Kullanıcı Adı</label
          >
          <input
            type="text"
            v-model="username"
            class="form-control"
          />
        </div>
        <div class="mb-3">
          <label class="form-label"
            >Şifre</label
          >
          <input ttype="password" v-model="pswrd" class="form-control" />
        </div>
        <div class="mb-3">
        </div>
      </form>
      <button @click="checkLogin" class="btn btn-primary centered button">Giriş yap</button>
    </div>
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

  methods: {
    checkLogin() {
      axios
        .get(
          "http://localhost:3000/users?password=" +
            this.pswrd +
            "&username=" +
            this.username
        )
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
<style scoped>
.centered {
  margin-top: 15%;
}
.centered button {
  margin-left: 34%;
  margin-top: -10% ;
}
.back{
  background-color: #edafb8 !important;
}
</style>