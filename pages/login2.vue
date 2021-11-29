<template>
  <div>
    <button @click="login">Login</button>
  </div>
</template>
<script>
export default {
  methods:{
    login(){
      this.$auth.loginWith('laravel/sanctum', {
        data: {
          email: 'admin@admin.com',
          password: '123123'
        }
      })
    }
  }
}
</script>
