<template>

  <div class=" row justify-center items-center">
    <q-card bordered class="q-pa-lg shadow-1">
      <q-card-section class="row items-center q-pb-none">
        <div class="text-h6"></div>
        <q-space />
        <q-btn icon="close" flat round dense v-close-popup class highlight />
      </q-card-section>
      <q-card-section class="text-h6" >
        Log In
      </q-card-section>
      <q-card-section>
        <q-form class="q-gutter-md">
          <q-input square filled clearable v-model="username" type="text" label="Username" />
          <q-input square filled clearable v-model="password" type="password" label="Password" />
        </q-form>
      </q-card-section>
      <q-card-actions class="q-px-md">
        <q-btn unelevated color="light-blue-7" size="lg" class="full-width" label="Login" @click="submitLogin"/>
      </q-card-actions>
      <q-card-section class="text-center q-pa-none">
        <p class="text-grey-6">Not registered yet?</p>
        <a href="/test">Create an Account</a>
      </q-card-section>
    </q-card>
  </div>

</template>

<script>
  import axios from 'app/node_modules/axios';
  import backendUrl from '../globals.js';
  export default {
    name: 'Login',
    data() {
      return {
        username:'',
        password: ''
      }
    },
    methods: {
      submitLogin: function (ev) {
          console.log(backendUrl);
        axios.post('http://localhost:8080/register', {
            username : this.username,
            password : this.password
        }).
        then(function (response) {
          console.log(JSON.parse(response))
        });
      }
    }
  }

</script>

<style>
  .q-card {
    width: 360px;
  }

</style>
