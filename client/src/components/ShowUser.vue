<template>
  <div>
    <h1>ข้อมูล Champagne</h1>
    <p>ขวดที่: {{ userId }}</p>
    <p>ชื่อ  {{ user.name }} - {{ user.lastname }}</p>
    <p>รายละเอียด: {{ user.email }}</p>
    <p>ราคา: {{ user.password }}</p>
  </div>
</template>
<script>
import UserService from "@/services/UsersService";
export default {
  data() {
    return {
      user: null,
    };
  },
  async created() {
    try {
      let userId = this.$route.params.userId;
      this.user = (await UserService.show(userId)).data;
    } catch (error) {
      console.log(error);
    }
  },
};
</script>
<style scoped>
</style>