<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated class="">
      <q-toolbar>


        <q-toolbar-title class="absolute-center">
          Awesome Todo
        </q-toolbar-title>


      </q-toolbar>
    </q-header>

    <q-drawer
      :width="225"
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      class="bg-primary"
      :breakpoint="767"
    >
      <q-list dark>
        <q-item-label
          header
        >
          Navigation
        </q-item-label>

        <q-item v-for="(nav,index) in navs"
          clickable :key="index"
          :to=nav.to
          class="text-grey-5"
          exact
        >
          <q-item-section

            avatar
          >
            <q-icon :name=nav.icon />
          </q-item-section>

          <q-item-section>
            <q-item-label>{{ nav.label }}</q-item-label>
          </q-item-section>
        </q-item>

      </q-list>
    </q-drawer>

    <q-footer>
      <q-tabs>
        <q-route-tab v-for="(nav,index) in navs" :key="index"
          :icon="nav.icon" :to="nav.to"
               :label="nav.label" />

      </q-tabs>
    </q-footer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>

import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'MainLayout',
  data() {
    return {

    }
  },
  components: {

  },

  setup () {
    const leftDrawerOpen = ref(false)
    let navs = ref([
      {
        label: 'Todo',
        icon: 'list',
        to: '/'
      },
      {
        label: 'Settings',
        icon: 'settings',
        to: '/settings'
      }
    ])
    return {
      leftDrawerOpen,
      navs,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>

<style lang="scss">
@media screen and (min-width: 768px){
  .q-footer{
    display: none;
  }
}
.q-drawer {
  .q-router-link--active{
      color: white !important;
      }
}
</style>

