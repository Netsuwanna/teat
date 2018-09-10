<template>
  <div>
    <center> <router-link :to="{ path: '/login'}" push><h1>ระบบจัดการเข้าสู่ระบบสำหรับผู้ดูแลระบบ</h1></router-link><br></center>
    <center><nuxt-link to="/table"><h1>ระบบแสดงข้อมูลสมชิก</h1></nuxt-link><br></center>
    <center><nuxt-link to="/search"><h1>ระบบค้นหาข้อมูลสมาชิก</h1></nuxt-link><br></center>
  </div>
</template>
<script>
export default {
  data() {
    return {
      id: 1
    };
  }
};
</script>
