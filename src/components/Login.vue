<template>
  <div>
    <form action=""></form>
    <label>username</label>
    <input type="text" v-model="username">
    <label>password</label>
    <input type="text" v-model="password">
    <input type="submit" @click="login()">
  </div>

</template>

<script>
import axios from "axios";
export default {
  name: "Login",
  data(){
    return{
      username: '',
      password: ''
    }
  },
  methods: {
    async login(){
      const row = {};
      row.fullName = this.fullName;
      row.email = this.email;
      axios.post('http://localhost:8081/nxp/v1/account/loginAc', row)
          .then(res => {
            // this.searchModalVisible = false;
            console.log('data: ' + res.data);
            this.$notify({
              group: 'foo',
              title: 'Alert',
              text: 'Success',
              duration: 3000,
            });
            this.close();
          })
          .catch(err => {
            console.log(err.response);
            this.$notify({
              group: 'foo',
              title: 'Alert',
              text: 'Not success',
              duration: 3000,

            });
          });
    }
  }
}
</script>

<style scoped>

</style>