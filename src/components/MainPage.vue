<script>
export default {
  name: 'MainPage',
  methods: {
    togglePage() {
      this.$emit('toggle-page');
    },
  },
}
</script>

<template>
  <div class="main-block">
    <p class="main-block__first-line">Пройдите точный и быстрый</p>

    <p class="main-block__title">
      Тест на <br>
      Определение <br>
      IQ
    </p>

    <button class="start-test" @click="togglePage">Пройти тест</button>

    <p class="main-block__text main-block__text--yellow">
      И получите рекомендации <br>
      по развитию своего интеллекта
    </p>
    <p class="main-block__text main-block__text--white">
      и улучшению финансового <br>
      благосостояния и личной жизни
    </p>

    <a class="main-block__more-button" href="#last-block">
      <img
        class="main-block__more-image" 
        src="../assets/icon.svg" 
        alt="arrow"
      >
    </a>

    <p class="main-block__more-text">
      Подробнее
    </p>
  </div>

  <div class="blue-block">
    <div class="blue-block__center">
      <div class="blue-block__items">
        <img 
          src="../assets/quotes.svg" 
          alt="quotes" 
          class="blue-block__quotes blue-block__quotes--1"
        >

        <img 
          src="../assets/quotes.svg" 
          alt="quotes"
          class="blue-block__quotes blue-block__quotes--2"
        >

        <p class="blue-block__description">
          Профессиональный <br> 
          IQ-тест позволяет не только определить коэффициент вашего интеллекта, <br> 
          но и выработать список рекомендаций для повышения этого показателя. 
        </p>
      </div>
    </div>
  </div>

  <div class="white-block">
    <p class="white-block__description">
      Также по результатам теста <br> 
      <b>ВЫ ПОЛУЧИТЕ</b> подробные 
      <b>СОВЕТЫ</b> по определению наиболее  перспективной 
      <b>ДЛЯ ВАШЕГО ТИПА интеллекта СФЕРЫ ДЕЯТЕЛЬНОСТИ,</b> <br>
      которая принесет вам скорейший финансовый результат.
    </p>

    <img src="../assets/325-01.svg" alt="image" class="white-block__image">
    
    <button class="start-test" @click="togglePage">Пройти тест</button>
  </div>

  <div class="last-block" id='last-block'>
    <p class="last-block__annotation">
      Прохождение теста займет у вас не более <span class="last-block__yellow-text">12 минут</span>, 
      а его результаты вы сможете <span class="last-block__yellow-text">использовать всю жизнь.</span>
    </p>

    <div class="last-block__grey-rectangle">
      Профессиональная интерпретация и детально <b>проработанные рекомендации</b>
      позволят вам качественно <b>изменить все аспекты своей жизни:</b>
      от финансового до любовного.
    </div>

    <button class="start-test start-test--transparent" @click="togglePage">Пройти тест</button>

    <p class="last-block__year-text">© 2019</p>

    <img 
      src="../assets/lightning_PNG9.svg" 
      alt="lightning" 
      class="last-block__light last-block__light--1"
    >

    <img 
      src="../assets/lightning_PNG9.svg" 
      alt="lightning" 
      class="last-block__light last-block__light--2"
    >
  </div>
</template>

<style lang="scss">
.container {
  display: flex;
  flex-direction: column
}

.navbar {
  height: 46px;
  background: #181818;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
}

.main-block {
  display: flex;
  flex-direction: column;
  text-align: center;
  align-items: center;
  width: 100%;
  height: calc(569px - 46px);
  background-image: url(../assets/rain_bk.svg);
  background-position: center;
  background-position: top;

  &__first-line {
    font-family: 'PT Serif', serif;
    font-weight: 400;
    font-size: 18px;
    line-height: 24px;
    color: #FFFFFF;
    letter-spacing: 0.05em;
    margin: 27px 0 0;
  }

  &__title {
    font-family: 'Yeseva One', cursive;
    font-size: 30px;
    line-height: 35px;
    letter-spacing: 0.03em;
    text-transform: uppercase;
    color: #FFC700;
    text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    margin: 20px 0 150px;
  }

  &__text {
    font-family: 'PT Serif';
    font-style: normal;
    font-weight: 700;
    font-size: 15px;
    line-height: 19px;
    text-align: center;
    letter-spacing: 0.05em;

    &--white {
      color: #FFFFFF;
    }

    &--yellow {
      color: #FFC700;
    }  
  }

  &__more-button {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 16px;
    height: 16px;
    background-color: #FFFFFF;
    border-radius: 50%;
    margin: 12px 0 5px;
  }

  &__more-text {
    font-family: 'PT Serif';
    font-style: normal;
    font-weight: 400;
    font-size: 8px;
    line-height: 11px;
    text-align: center;
    letter-spacing: 0.05em;
    color: #FFFFFF;
  }

  &__more-image {
    width: 8px;
    height: 8px;
  }
}

.blue-block {
  height: 339px;
  background-image: url(../assets/image.svg);
  background-size: cover;
  background-position: center;
  
  &__center {
    display: flex;
    justify-content: center;
    height: 339px;
    background: radial-gradient(
      84.34% 50.29% at 48.75% 49.71%, 
      #2950C2 0%, rgba(38, 91, 199, 0.96) 40.62%,
      rgba(39, 98, 187, 0) 85.42%
    )
  }

  &__items {
    position: relative;
    width: 320px;
  }

  &__description {
    font-family: 'Yeseva One';
    font-style: normal;
    font-weight: 400;
    font-size: 18px;
    line-height: 23px;
    text-align: center;
    letter-spacing: 0.05em;
    color: #FFFFFF;
    width: 248px;
    padding: 83px 36px 0 36px;
  }

  &__quotes {
    position: absolute;
    width: 23px;
    height: 22.35px;

    &--1 {
      top: 43px;
      left: 24.35px;
    }
    
    &--2 {
      right: 29px;
      bottom: 32px;
      transform: rotate(-180deg);
    }
  }
}

.white-block {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 38px 11px 20px;
  background-color: #FFFFFF;

  &__description {
    max-width: 300px;
    font-family: 'PT Serif';
    font-style: normal;
    font-weight: 400;
    font-size: 16px;
    line-height: 24px;
    letter-spacing: 0.05em;
    color: #272727;
    margin-bottom: 38px;
  }

  &__image {
    width: 232px;
  }
}

.last-block {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 533px;
  background-image: url(../assets/rain_bk2.svg);
  padding: 0 12px;
  position: relative;
  overflow: hidden;

  &__annotation {
    max-width: 320px;
    font-family: 'Merriweather';
    font-style: normal;
    font-weight: 400;
    font-size: 15px;
    line-height: 20px;
    letter-spacing: 0.05em;
    color: #FFFFFF;
    margin: 56px 2px 20px;
  }

  &__yellow-text {
    color: #FFC700;
  }

  &__grey-rectangle {
    max-width: 304px;
    background: rgba(243, 243, 242, 0.8);
    border-radius: 20px;
    padding: 30px 14px;
    font-family: 'Merriweather';
    font-style: normal;
    font-weight: 400;
    font-size: 16px;
    line-height: 23px;
    letter-spacing: 0.05em;
    color: #181818;
    margin-bottom: 33px;
    z-index: 2;
  }

  &__light {
    position: absolute;
    width: 165px;
    height: 165px;

    &--1 {
      right: -20px;
      top: 64px;
      transform: rotate(19.42deg);
    }

    &--2 {
      left: -80px;
      bottom: 32px;
      transform: rotate(-55.55deg)
    }
  }

  &__year-text {
    font-family: 'Roboto';
    font-style: normal;
    font-weight: 400;
    font-size: 10px;
    line-height: 23px;
    text-align: center;
    letter-spacing: 0.05em;
    color: rgba(255, 255, 255, 0.5);
    margin: 42px 0 13px;
  }
}

.start-test {
  width: 189px;
  height: 41px;
  background: radial-gradient(50% 50% at 50% 50%, #FFC700 0%, #FFC700 100%);
  border-radius: 20px;
  color: #0D0C11;
  font-family: 'Merriweather';
  font-weight: 700;
  font-size: 14px;
  line-height: 18px;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  margin-bottom: 20px;
  border: none;
  cursor: pointer;

  &--transparent {
    color: #FFFFFF;
    border: 1px solid #FFFFFF;
    background: transparent;
  }
}
</style>