<template>
  <v-container>
    <v-layout column>
      <v-flex xs6 offset-xs3>
        <div class="white elevation-2">
          <v-toolbar flat dense class="cyan" xs6 dark>
            <v-toolbar-title>Register</v-toolbar-title>
          </v-toolbar>
        </div>

        <div class="pl-4 pr-4 pt-2 pb-2">
          <h1>Register</h1>
          <input type="email" name="email" placeholder="Email" v-model="email" />
          <br />
          <input type="password" name="password" placeholder="Password" v-model="password" />
          <br />
          <div class="error" v-html="error" />
          <br />
          <v-btn @click="register">Register</v-btn>
        </div>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'
export default {
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    async register () {
      try {
        await AuthenticationService.register({
          email: this.email,
          password: this.password
        })
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
 .error {
   color: red;
 }
</style>
