<template>
  <q-layout style="background-color: #7a776f" view="lHh Lpr lFf">
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
          Corona Vírus Brasil
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-1"
    >
      <q-list v-for="m in menu" v-bind:key="m.label">
        <q-item clickable @click="routeTo(m.routeName)">
          <q-item-section avatar>
            <q-icon :name="m.icon" />
          </q-item-section>

          <q-item-section>
            <q-item-label>{{ m.label }}</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <transition
        name="transitions"
        enter-active-class="animated zoomIn"
        leave-active-class="animated zoomOut"
        mode="out-in"
      >
        <router-view />
      </transition>
    </q-page-container>
    <q-footer style="padding:.3em">
      <small>Developer by Jhonatan Froeder</small>
    </q-footer>
  </q-layout>
</template>

<script>
export default {
  name: "MainLayout",

  components: {},

  data() {
    return {
      leftDrawerOpen: false,
      menu: [
        {
          label: "Home",
          routeName: "HomeScreen",
          icon: "home"
        },
        {
          label: "Sobre",
          routeName: "AboutScreen",
          icon: "info"
        }
      ]
    };
  },
  methods: {
    routeTo(routeName) {
      console.log(routeName);
      this.$router.push({ name: routeName });
    }
  }
};
</script>
