<template>
  <q-layout view="hHh lpR lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          <div class="absolute-center">
             <q-icon name="savings" />
         Moneyballs 
          </div>
         
        </q-toolbar-title>

      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      class="bg-primary"
      show-if-above
      bordered
    >
      <q-list>
        <q-item-label
        class="text-white"
          header
        >
          Navigation 
        </q-item-label>

        <NavLink
          v-for="link in navLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import NavLink, {NavLinkProps} from 'components/Nav/NavLink.vue';

defineOptions({
  name: 'MainLayout'
});

const navLinks: NavLinkProps[] = [
  {
    title: 'Docs',
    icon: 'school',
    link: 'https://quasar.dev'
  },
  {
    title: 'Github',
    icon: 'code',
    link: 'https://github.com/quasarframework'
  },
];

const leftDrawerOpen = ref(false);

function toggleLeftDrawer () {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>
