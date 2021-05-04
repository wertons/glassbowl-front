<template>

  <div class=" row justify-center items-center">
    <q-card bordered class="q-pa-lg shadow-1">
      <q-card-section class="row items-center q-pb-none">
        <div class="text-h6"></div>
        <q-space />
        <q-btn icon="close" flat round dense v-close-popup class highlight />
      </q-card-section>
      <q-card-section class="text-h6">
        Create new School
      </q-card-section>
      <q-card-section>
        <q-form class="q-gutter-md">
          <q-input square filled clearable v-model="title" type="text" label="Title" />
        </q-form>
      </q-card-section>
      <q-card-actions class="q-px-md">
        <q-btn unelevated color="light-blue-7" size="lg" class="full-width" label="Create School"
          @click="submitSchool" />
      </q-card-actions>

    </q-card>
  </div>

</template>

<script>
  import axios from 'app/node_modules/axios';
  export default {
    name: 'SchoolCreator',
    data() {
      return {
        title: '',
        token: localStorage.getItem('utoken')
      }
    },
    methods: {
      submitSchool: function (ev) {
        axios.post('http://localhost:8080/school', {
          title: this.title,
        }, {
          headers: {
            token: this.token
          }
        }).
        then(function (response) {
          console.log(JSON.parse(response))
        });
      }
    }
  }

</script>

<style>

</style>
