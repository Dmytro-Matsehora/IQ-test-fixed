<script>
  import Loader from './Loader.vue';

  export default {
    name: 'TestPage',
    components: {
      Loader,
    },
    props: {
      page: Number
    },
    data() {
      return {
        data: [
          { 
            key: 1,
            question: "Ваш пол:",
            answers: ["Мужчина", "Женщина"]
          },
          {
            key: 2,
            question: "Укажите ваш возраст:",
            answers: ["До 18", "От 18 до 28", "От 18 до 35", "От 36"]
          },
          {
            key: 3,
            question: "Выберите лишнее:",
            answers: ["Дом", "Шалаш", "Бунгало", "Скамейка", "Хижина"]
          },
          {
            key: 4,
            question: "Продолжите числовой ряд: 18 20 24 32",
            answers: ["62", "48", "74", "57", "60", "77"]
          },
          {
            key: 5,
            question: "Выберите цвет, который сейчас наиболее Вам приятен:",
            answers: ["grey", "blue", "green", "red", "yellow", "brown", "black", "purple", "aquamarine"],
            type: "colors",
          }, 
          {
            key: 6,
            question: "Отдохните пару секунд, еще раз выберите цвет, который сейчас наиболее Вам приятен:",
            answers: ["grey", "aquamarine", "brown", "green", "black", "red", "purple", "yellow", "blue"],
            type: "colors",
          },
          {
            key: 7,
            question: "Какой из городов лишний?",
            answers: ["Вашингтон", "Лондон", "Париж", "Нью-Йорк", "Москва", "Оттава"]
          },
          {
            key: 8,
            question: "Выберите правильную фигуру из четырёх пронумерованных:",
            image: "TQ-8_image.svg",
            answers: ["1", "2", "3", "4"],
            type: "squares"
          },
          {
            key: 9,
            question: "Вам привычнее и важнее:",
            answers: [
              "Наслаждаться каждой минутой проведенного времени", 
              "Быть устремленными мыслями в будущее", 
              "Учитывать в ежедневной практике прошлый опыт", 
            ],
          },
          {
            key: 10,
            question: "Какое определение, по-Вашему, больше подходит к этому геометрическому изображению:",
            image: "TQ-10_image.svg",
            answers: [
              "Оно остроконечное", 
              "Оно устойчиво", 
              "Оно находится в состоянии равновесия", 
            ],
          },
          {
            key: 11,
            question: "Какое определение, по-Вашему, больше подходит к этому геометрическому изображению:",
            image: "TQ-11_image.svg",
            answers: ["34", "36", "53", "44", "66", "42"],
            type: 'squares'
          }
        ],
        buttonDisabled: true,
        progress: 8,
      };
    },
    computed: {
      progressBarWidth() {
        return `${this.progress}%`;
      },
      lastPage() {
        return this.data[this.data.length - 1].key + 1;
      }
    },
    methods: {
      togglePage() {
        this.$emit('toggle-page');
        this.buttonDisabled = true;
        this.progress += 8;
      },
      buttonDisable() {
        this.buttonDisabled = false;
      }
    }
  }
</script>

<template>
  <div class="question-container">
    <div class="progress-bar">
      <div class="progress-bar__fill" :style="{ width: progressBarWidth }">
      </div>
    </div>

    <form class="question" 
      v-for="item in data" 
      :key="item.key" 
      v-show="item.key === page"
    >
      <h1 class="question__title">
        {{item.question}}
      </h1>

      <img 
        v-if="item.image"
        class="question__image"
        :src="item.image" 
        alt="question__image"
      >

      <div 
        :class="{ 
          'options': !item.type, 
          'question__square-container': (item.type === 'colors' || item.type === 'squares' ) 
        }"
      >
        <div v-for="(answer, index) in item.answers" :key="index">
          <input 
            type="radio" 
            :id="'radio_' + item.key + '_' + index"
            :name="'radio_' + item.key"
            :class="{ 
              'question__radio-button': !item.type,
              'question__radio-square': (item.type === 'colors'),
              'question__radio-little-square': (item.type === 'squares') 
            }"
          >

          <label 
            :class="{ 
              'question__option': !item.type, 
              'question__square': (item.type === 'colors'),
              ['question__square--' + answer]: (item.type === 'colors'),
              'question__little-square': (item.type === 'squares') 
            }"
            :for="'radio_' + item.key + '_' + index" 
            @click="buttonDisable"
          > 
            {{(!item.type || item.type === 'squares') ? answer : ""}}
          </label>
        </div>
      </div>
    </form>

    <Loader 
      v-if="page === lastPage"
      @toggle-page="togglePage"
    />

    <button 
      v-if="page < lastPage"
      class="button-next" 
      :disabled="buttonDisabled"
      @click="togglePage"
    >
      Далее
    </button>
  </div>
</template>

<style lang="scss">
  .question-container {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    height: calc(100vh - 48px - 70px);
    background-image: url(../assets/rain_bk2.svg);
  }

  .progress-bar {
    width: 260px;
    height: 11px;
    margin: 17px 0;
    background-color: rgba(242, 243, 243, 0.59);
    mix-blend-mode: normal;
    border-radius: 10.5px;

    &__fill {
      z-index: 2;
      height: 100%;
      background: #3BDE7C;
      border-radius: 10.5px;
    }
  }
  
  .button-next {
    min-height: 41px;
    width: 189px;
    height: 41px;
    background: radial-gradient(50% 50% at 50% 50%, #FFC700 0%, #FFC700 100%);
    color: #0D0C11;
    box-shadow: inset 0px 4px 10px rgba(0, 0, 0, 0.25);
    border-radius: 20px;
    font-family: 'Merriweather';
    font-style: normal;
    font-weight: 700;
    font-size: 14px;
    line-height: 18px;
    text-align: center;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin: 25px 0 25px;
    border: none;
    cursor: pointer;

    &:disabled {
      background: #DADADA;
      color: #8E8E8E;
    }
  }

  .options {
    width: 100%;
  }
</style>