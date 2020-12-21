<template>
<!-- örnek olabilir diye yaptım  -->
  <div class="card card-light w-40">
    <div class="card--header">
      <h3>Aktif Kullanıcılar</h3>
    </div>
    <div class="card--body" v-for="i in userInfo" :key="i.id">
      <div
        class="active-user-item d-flex justify-content-start align-items-center"
      >
      <img class="rounded-circle mr-5" :src="i.img" />
       
        <div class="full_name" >
          {{ i.username }}
          
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: ["userInfo"],
};
</script>

<style scoped>
</style>