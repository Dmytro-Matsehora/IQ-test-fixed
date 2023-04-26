<script>
  import Timer from "../utils/Timer.vue";

  export default {
    name: 'ResultPage',
    components: {
      Timer,
    },
    data() {
      return {
        character: {},
        showTable: false,
      };
    },
    methods: {
      getData() {
        fetch("https://swapi.dev/api/people/1/")
          .then(response => response.json())
          .then(data => {
            const { name, height, mass, hair_color, skin_color, eye_color, birth_year, gender } = data
            this.character = { name, height, mass, hair_color, skin_color, eye_color, birth_year, gender };
          } )
          .catch(error => console.error(error));

        this.showTable = true;
      },
    }
};
</script>

<template>
  <div class="result-container">
    <div class="title-block">
      <h1 class="title-block__title">
        Ваш результат рассчитан:
      </h1>
      
      <p class="title-block__description">
        <span class="title-block__underline">Вы относитесь к 3%</span> 
        респондентов, чей уровень интеллекта более чем на 15 пунктов 
        отличается от среднего в большую или меньшую сторону! 
      </p>
    </div>
    

    <div class="timer-block">
      <h2 class="timer-block__title">
        Скорее получите свой результат!
      </h2>

      <div class="timer-block__description">
        В целях защиты персональных данных результаты теста, их подробная интерпретация 
        и рекомендации доступны в виде голосового сообщения по звонку с вашего мобильного телефона
      </div>

      <div class="timer-block__timer-text">
        Звоните скорее, запись доступна всего <br>
        <span class="timer-block__timer"> 
          <Timer />
        </span> минут
      </div>
    </div>

    <button class="call-button" @click="getData">
      <img 
        class="call-button__image"
        src="../assets/Phone-icon.svg" 
        alt="phone"
      >
        Позвонить и прослушать результат 
    </button>

    <table class="info-table" v-if="showTable">
      <tbody>
        <tr class="info-table__column" v-for="(value, key) in character" :key="key">
          <td class="info-table__row" >{{ key }}:</td>
          <td class="info-table__row" >{{ value }}</td>
        </tr>
      </tbody>
    </table>

    <img src="../assets/lightning_PNG9.svg" alt="lightning" class="light1">
    <img src="../assets/lightning_PNG9.svg" alt="lightning" class="light2">
  </div>

  <div :class="{ 'footer': showTable, 'footer2': !showTable }">
    TERMENI SI CONDITII: ACESTA ESTE UN SERVICIU <br>
    DE DIVERTISMENT. PRIN FOLOSIREA LUI <br>
    DECLARATI CA AVETI 18 ANI IMPLINITI <br>
    TERMENI SI CONDITII: ACESTA ESTE UN SERVICIU <br>
    DE DIVERTISMENT. PRIN FOLOSIREA LUI <br>
    DECLARATI CA AVETI 18 ANI IMPLINITI <br>
    TERMENI SI CONDITII: ACESTA ESTE UN SERVICIU <br>
    DE DIVERTISMENT. PRIN FOLOSIREA LUI <br>
    DECLARATI CA AVETI 18 ANI IMPLINITI <br>
    TERMENI SI CONDITII: ACESTA ESTE UN SERVICIU <br>
    DECLARATI CA AVETI 18 ANI IMPLINITI <br>
    DE DIVERTISMENT. PRIN FOLOSIREA LUI <br>
  </div>
</template>

<style lang="scss">
  .result-container {
    position: relative;
    display: flex;
    overflow: hidden;
    min-height: calc(100vh - 47px);
    flex-direction: column;
    align-items: center;
    background-image: url("../assets/rain_bk2.svg");
  }

  .title-block {
    padding-top: 36px;
    margin-bottom: 22px;

    &__title {
      margin-bottom: 16px;
      font-family: 'PT Serif';
      font-style: normal;
      font-weight: 700;
      font-size: 15px;
      line-height: 16px;
      text-align: center;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: #FFFFFF;
    }

    &__description {
      padding: 0 5px;
      max-width: 600px;
      font-family: 'PT Serif';
      font-style: normal;
      font-weight: 400;
      font-size: 14px;
      line-height: 18px;
      text-align: center;
      color: #FFFFFF;
    }

    &__underline {
      text-decoration: underline;
    }
  }

  .timer-block {
    display: flex;
    flex-direction: column;
    align-items: center;

    &__title {
      font-family: 'PT Serif';
      font-style: normal;
      font-weight: 700;
      font-size: 18px;
      line-height: 22px;
      text-align: center;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: #3BDE7C;
      margin-bottom: 12px;
    }

    &__description {
      width: 256px;
      padding: 12px;
      background: #1C2741;
      border-radius: 6px;
      font-family: 'Roboto';
      font-style: normal;
      font-weight: 500;
      font-size: 8px;
      line-height: 14px;
      text-align: center;
      letter-spacing: 2px;
      text-transform: uppercase;
      color: #FFFFFF;
      margin-bottom: 12px;
    }

    &__timer-text {
      font-family: 'PT Serif';
      font-style: normal;
      font-weight: 400;
      font-size: 11px;
      text-align: center;
      letter-spacing: 0.1em;
      color: #3BDE7C;
      margin-bottom: 10px;
    }

    &__timer {
      font-size: 20px;
      padding: 0 10px;
    }
  }

  .call-button {
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: left;
    padding: 15px;
    width: 290px;
    height: 92px;
    background: #EB1B00;
    border-radius: 5px;
    border-style: none;
    font-family: 'Roboto';
    font-style: normal;
    font-weight: 900;
    font-size: 15px;
    line-height: 18px;
    letter-spacing: 0.05em;
    color: #FFFFFF;
    margin-bottom: 20px;
    z-index: 2;
    cursor: pointer;

    &__image {
      margin-right: 18px;
    }
  }

  .info-table {
    display: block;
    color: #FFFFFF;
    background: #1C2741;
    margin-bottom: 20px;
    font-family: 'PT Serif';
    font-style: normal;
    font-weight: 400;
    font-size: 14px;
    line-height: 18px;
    text-align: center;
    color: #FFFFFF;

    &__row {
      border: 2px solid black;
      padding: 5px 10px;
    }
  }

  .light1 {
    position: absolute;
    width: 165px;
    height: 165px;
    right: -20px;
    bottom: 80px;
    transform: rotate(19.42deg);
  }

  .light2 {
    position: absolute;
    width: 165px;
    height: 165px;
    left: -80px;
    bottom: 45px;
    transform: rotate(-55.55deg)
  }

  .footer {
    align-self: center;
    font-family: 'Roboto';
    font-style: normal;
    font-weight: 400;
    font-size: 7px;
    line-height: 9px;
    text-align: center;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: rgba(255, 255, 255, 0.5);
  }

  .footer2 {
    align-self: center;
    font-family: 'Roboto';
    font-style: normal;
    font-weight: 400;
    font-size: 7px;
    line-height: 9px;
    text-align: center;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: rgba(255, 255, 255, 0.5);
    position: absolute;
    left: 0;
    right: 0;
    bottom: -90px;
  }
</style>