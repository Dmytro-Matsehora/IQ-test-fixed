<script>
  import TestPage from './components/TestPage.vue';
  import MainPage from './components/MainPage.vue';
  import NavMenu from './components/NavMenu.vue';
  import NavBar from './components/NavBar.vue';
  import ResultPage from './components/ResultPage.vue';

  export default {
    name: 'App',
    components: {
      TestPage,
      MainPage,
      NavMenu,
      NavBar,
      ResultPage,
    },
    data() {
      return {
        isMenuOpen: false,
        showPage: 0,
      };
    },
    methods: {
      toggleMenu() {
        this.isMenuOpen = !this.isMenuOpen;
      },
      togglePage() {
        this.showPage += 1;
      },
      backToMain() {
        this.showPage = 0
      }
    },
  };
</script>

<template>
  <NavBar
    v-if="!isMenuOpen"
    :page="showPage"
    @toggle-menu="toggleMenu"
  />

  <NavMenu 
    :class="{ 'is-active': isMenuOpen }"
    :page="showPage"
    @toggle-menu="toggleMenu"
    @toggle-page="togglePage"
    @back-to-main="backToMain"
  />


  <MainPage 
    v-if="showPage === 0 && !isMenuOpen" 
    :page="showPage"
    @toggle-page="togglePage"
  />

  <TestPage
    v-if="showPage > 0 && showPage < 13 && !isMenuOpen"
    :page="showPage"
    @toggle-page="togglePage"
  />

  <ResultPage
    v-if="showPage === 13 && !isMenuOpen" 
    :page="showPage"
    @toggle-page="togglePage"
  />
</template>

<style>
  .fade-enter-active,
  .fade-leave-active {
    transition: opacity 2s;
  }

  .fade-enter,
  .fade-leave-to {
    opacity: 0;
  }
</style>
