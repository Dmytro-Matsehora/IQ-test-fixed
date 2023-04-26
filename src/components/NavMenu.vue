<script>
  export default {
    name: 'NavMenu',
    props: {
      page: Number,
    },
    methods: {
      toggleMenu() {
        this.$emit('toggle-menu');
      },
      togglePage() {
        this.$emit('toggle-page');
      },
      startTest() {
        this.toggleMenu();
        if (this.page === 0) {
          this.togglePage();
        }  
      },
      backToMain() {
        this.$emit('back-to-main');
        this.toggleMenu();
      }
    }
  }
</script>

<template>
  <div class="nav-menu">
    <button class="cross-button" @click="toggleMenu">
      <img class="cross-button__image" src="../assets/cross-icon.svg" alt="cross">
    </button>

    <a href="#" class="nav-menu__item" @click="backToMain">
      Главная
    </a>

    <a href="#last-block" class="nav-menu__item" @click="backToMain">
      Информация о тесте
    </a>

    <a href="#" class="nav-menu__item" @click="startTest">
      Пройти тест
    </a>
  </div>
</template>

<style lang="scss">
  .nav-menu {
    display: none;
    height: 100vh;
    z-index: 20;
    background-color: #181818;
    box-shadow: 0 2px 3px rgba(10, 10, 10, 0.2);

    &.is-active {
      display: flex;
      flex-direction: column;
    }

    &__item {
      text-decoration: none;
      font-family: 'Roboto';
      font-style: normal;
      font-weight: 300;
      font-size: 16px;
      line-height: 22px;
      text-transform: uppercase;
      color: #FFFFFF;
      margin: 0 0 27px 23px;
    }

    &__item:hover {
      color: #FFC700;
    }
  }

  .cross-button {
    margin: 18px 13px 64px auto;
    padding: 0;
    background-color: transparent;
    border: none;
    cursor: pointer;

    &__image {
      display: block;
    }
  }
</style>