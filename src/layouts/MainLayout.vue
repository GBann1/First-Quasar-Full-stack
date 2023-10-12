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
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title> Notes 'n Tasks' </q-toolbar-title>

        <div>
          <q-avatar>
            <img
              src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fthehappypuppysite.com%2Fwp-content%2Fuploads%2F2019%2F04%2FBelgian-Malinois-German-Shepherd-Mix-HP-long.jpg&f=1&nofb=1&ipt=54cd3e8d8757847536b2ab7d8edd9ace0e4312c9d033abed124ad7dc881381a6&ipo=images"
            />
          </q-avatar>
        </div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header> Sections </q-item-label>

        <EssentialLink
          v-for="link in essentialLinks"
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

<script>
import { defineComponent, ref } from "vue";
import EssentialLink from "components/EssentialLink.vue";

const linksList = [
  {
    title: "E-mail",
    caption: "Gmail Inbox",
    icon: "mail",
    link: "https://mail.google.com",
  },
  {
    title: "Github",
    caption: "github.com/GBann1",
    icon: "code",
    link: "https://github.com/GBann1",
  },
  {
    title: "Notes",
    icon: "note",
    link: "~/#/404",
  },
  {
    title: "Tasks",
    icon: "task",
    link: "~/#/404",
  },
];

export default defineComponent({
  name: "MainLayout",

  components: {
    EssentialLink,
  },

  setup() {
    const leftDrawerOpen = ref(false);

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
});
</script>
