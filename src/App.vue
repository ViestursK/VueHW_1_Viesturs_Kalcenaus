<!-- App.vue -->
<template>
    <HeaderComponent @login="handleLogin" />
    <div class="grid" v-if="isLoggedIn">
      <NavigationComponent :activeTab="activeTab" :isLoggedIn="isLoggedIn" @changeTab="changeTab" />
      <component :is="activeTab" />
    </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import NavigationComponent from './components/NavigationComponent.vue';
import HomeComponent from './components/HomeComponent.vue';
import AboutMeComponent from './components/AboutMeComponent.vue';

export default {
  name: 'App',
  components: {
    HeaderComponent,
    NavigationComponent,
    AboutMeComponent,
    HomeComponent,
  },
  data() {
    return {
      isLoggedIn: false,
      activeTab: HomeComponent
    };
  },
  methods: {
    handleLogin(isLoggedIn) {
      this.isLoggedIn = isLoggedIn;
      this.activeTab = 'home';
    },
    changeTab(tab) {
      this.activeTab = tab;
    },
  },
};
</script>

<style>
body {
  margin: 0;
  background-color: #1e1e2e;
  color: #f0f0f0;
  font-family: 'Arial', sans-serif;
  height: 100vh;
  display: flex;
}

.grid {
  margin-top: 10vh;
  display: grid;
  grid-template-columns: 1fr 1fr;
  height: 100%;
}

.column {
  height: 100%;
  overflow: auto;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}
</style>

