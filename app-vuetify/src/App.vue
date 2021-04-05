<template>
  <v-app>
    <v-card width="400px" class="mt-5 mx-auto" elevation="5">
      <v-card-title>
        <h1>Login</h1>
      </v-card-title>
      <v-card-text>
        <v-form>
          <v-text-field 
            label="Username"
            prepend-icon="mdi-account-circle"
            v-model="username"
          />
          <label for="">{{username}}</label>
          <v-text-field
            v-bind:type="showPassword"
            label="Password"
            prepend-icon="mdi-lock"
            v-bind:append-icon="visibilityICON"
            v-model="password"
            v-on:click:append='showData = !showData'
          />
          <label for="">{{password}}</label>
        </v-form>
      </v-card-text>
      <v-divider></v-divider>
      <v-card-actions>
        <v-btn color="success">Register</v-btn>
        <v-spacer></v-spacer>
        <v-btn color="info">Login</v-btn>
      </v-card-actions>
    </v-card>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      username: null,
      password: null,
      showData: false
    }
  },
  computed: {
    showPassword(){
      if(this.showData){
          return 'text'
        } else {
          return 'password'
        }
    },
    visibilityICON(){
      if(this.showData){
          return 'mdi-eye'
        } else {
          return 'mdi-eye-off'
        }
    }
  }
};
</script>

<style>

</style>
