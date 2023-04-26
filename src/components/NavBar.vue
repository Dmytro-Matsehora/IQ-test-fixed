<script>
  export default {
    name: 'NavBar',
    props: {
      page: Number,
    },
    methods: {
      toggleMenu() {
        this.$emit('toggle-menu');
      },
    }
  }
</script>

<template>
    <div class="navbar">
      <button class="navbar__burger" @click="toggleMenu">
        <span class="navbar__rectangle"></span>
        <span class="navbar__rectangle"></span>
        <span class="navbar__rectangle"></span>
      </button>

      <div class="navbar__content" v-if="page > 0">
        <img 
          class="navbar__logo"
          src="../assets/rain_bk3.svg" 
          alt="brain"
        >

        <p class="navbar__text" v-if="page < 13">
          Тест на определение IQ
        </p>

        <p class="navbar__text navbar__text--2" v-if="page === 13">
          Готово!
        </p>
      </div>
    </div>

</template>

<style lang="scss">
  .navbar {
    display: flex;
    height: 46px;
    background: #181818;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);

    &__burger {
      display: block;
      position: relative;
      padding: 0;
      margin: 15px;
      border: none;
      background-color: transparent;
      cursor: pointer;
    }

    &__rectangle {
      display: block;
      width: 24px;
      height: 2.7px;
      margin-bottom: 4px;
      background: #DADADA;
      transition: transform 0.2s ease-out;
    }

    &__burger span:last-child {
      margin-bottom: 0;
    }

    &__content {
      display: flex;
      text-align: center;
      justify-content: center;
      align-items: center;
    }

    &__logo {
      width: 48px;
      height: 47px;
      margin-right: 9px;
    }

    &__text {
      font-family: 'Yeseva One';
      font-style: normal;
      font-weight: 400;
      font-size: 12px;
      line-height: 14px;
      letter-spacing: 0.05em;
      text-transform: uppercase;
      color: #FFC700;
      margin-top: 4px;

      &--2 {
        font-size: 20px;
        line-height: 23px;
        letter-spacing: 0.1em;
        margin-left: 24px;
      }
    }
  }
</style>