<template>

  <div class=" row justify-center ">
    <q-card bordered class="q-pa-lg shadow-1">
      <q-card-section class="row items-center q-pb-none">
        <div class="text-h6"></div>
        <q-space />
        <q-btn icon="close" flat round dense v-close-popup class highlight />
      </q-card-section>
      <q-card-section class="text-h6" >
        Register
      </q-card-section>
      <q-card-section>
        <q-form class="q-gutter-md">
          <div>
          <q-input square filled clearable v-model="email" type="email" label="Email" @focus="emailTooltip = true" />
                    <q-tooltip v-model="emailTooltip"  anchor="center right" self="center left" >Must be a valid email</q-tooltip>
          </div>
          <div>
          <q-input square filled clearable v-model="username" type="text" label="Username" @focus="usernameTooltip = true" />
                    <q-tooltip v-model="usernameTooltip" anchor="center right" self="center left">Must be unique and contain at least 3 characters</q-tooltip>
          </div>
          <div>
          <q-input square filled clearable v-model="nickname" type="text" label="Nickname" @focus="nicknameTooltip = true" />
                    <q-tooltip v-model="nicknameTooltip" anchor="center right" self="center left">Non mandatory</q-tooltip>
          </div>
          <div>
          <q-input square filled clearable v-model="password" type="password" label="Password" @focus="passwordTooltip = true" />
                    <q-tooltip v-model="passwordTooltip" anchor="center right" self="center left">Must contain at least ? characters</q-tooltip>
          </div>
        </q-form>
      </q-card-section>
      <q-card-actions class="q-px-md">
        <q-btn unelevated color="light-blue-7" size="lg" class="full-width" label="Register" @click="submitRegister"/>
      </q-card-actions>
      <q-card-section class="text-center q-pa-none">
        <p class="text-grey-6">Already registered?</p>
        <a href="/test">Log In</a>
      </q-card-section>
    </q-card>
  </div>

</template>

<script>
  import axios from 'app/node_modules/axios';
  import {backendUrl} from 'app/src/globals';
  export default {
    name: 'Register',
    data() {
      return {
        username:'',
        usernameTooltip:false,
        password: '',
        passwordTooltip:false,
        email: '',
        emailTooltip:false,
        nickname:'',
        nicknameTooltip:false
      }
    },
    methods: {
      submitRegister: function (ev) {
        axios.post('http://localhost:8080/register', {
            username : this.username,
            password : this.password,
            email : this.email,
            nickname: this.nickname
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
