<template>
  <!-- <p> active user: {{toUser}} </p> -->
  <!-- örnek olabilir diye yaptım  -->
  <div class="card card-light w-40">
    <div class="card--header">
      <h3>Aktif Kullanıcılar</h3>
    </div>
    <div
      class="card--body list-group"
      @click="changeValue(i)"
      v-for="i in userList"
      :key="i.id"
    >
      <div
        class="active-user-item d-flex justify-content-start align-items-center"
      >
        <div
          class="badge d-flex justify-content-center align-items-center mr-5"
        >
          <img class="rounded-circle mr-5" :src="i.img" />
        </div>
        <button
          type="button"
          class="list-group-item list-group-item-action"
          aria-current="true"
        >
          {{ i.username }}
        </button>
      </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      userList: [],
      selectUser: [],
      toUser: null,
    };
  },
  methods: {
    changeValue(e) {
      this.toUser = e;
      this.$emit("toUserChange", this.toUser);
      console.log("changevalue  ", this.toUser.id);
    },
  },
  created() {
    axios
      .get("http://localhost:3000/users")
      .then((response) => {
        console.log("active list users", response);
        this.userList.push(...response.data);
      })
      .catch((e) => {
        console.log("e", e);
      });
  },
};
</script>

<style scoped>
</style>