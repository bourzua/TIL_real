<template>
  <div>
    <h1>SIGN UP</h1>
    <div>
      <label for="username">사용자 이름: </label>
      <input type="text" id="username" v-model="credentials.username">
    </div>
    <div>
      <label for="password">비밀번호: </label>
      <input type="password" id="password" v-model="credentials.password">
    </div>
    <div>
      <label for="passwordConfirmation">비밀번호 확인: </label>
      <input type="password" id="passwordConfirmation" v-model="credentials.passwordConfirmation"
      @keypress.enter="signup">
    </div>
    <button @click="signup">Signup</button>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Signup',
  data() {
    return{
      credentials: {
        username: '',
        password: '',
        passwordConfirmation: '',
      }
    }
  },
  methods: {
    signup() {
      axios.post('http://127.0.0.1:8000/accounts/signup/', this.credentials)
        .then((res)=>{
          console.log(res)
          this.$router.push({ name: 'Login' })
        })
        .catch((err)=>{
          console.log(err)
        })
    }
  },
}
</script>

<style>

</style>