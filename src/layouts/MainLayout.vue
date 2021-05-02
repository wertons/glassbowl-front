<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title>
          Glassbowl
        </q-toolbar-title>

      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-1"
    >
      <q-list>
        <q-item-label
          header
          class="text-grey-8"
        >
          Menu
        </q-item-label>

      </q-list>
    </q-drawer>

    <q-page-container>
      <div @click="login = true">test</div>

      <router-view />
    </q-page-container>
      <q-dialog v-model="login" persistent>
        <Login />
      </q-dialog>
  </q-layout>
</template>

<script>
import Login from 'components/Login.vue'




export default {
  name: 'MainLayout',
  components: {  Login },
  data () {
    return {
      leftDrawerOpen: false,
      login: false
    }
  }
}
</script>
