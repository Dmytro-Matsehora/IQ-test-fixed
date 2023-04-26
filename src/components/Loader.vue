<script>
  export default {
    name: 'Loader',
    methods: {
      buttonDisable() {
        this.$emit('button-disable');
      }
    },
    mounted() {
    setTimeout(() => {
      this.$emit('toggle-page');
    }, 5000);
  },
  }
</script>

<template>
  <div class="question">
    <h1 class="question__title question__title--big">
      Обработка <br>
      результатов
    </h1>

    <div class="loader">
      <div></div> <div></div> <div></div>
      <div></div> <div></div> <div></div>
      <div></div> <div></div> <div></div>
      <div></div> <div></div> <div></div>
    </div>
  </div>

  <div class="loading-dots">
    Определение стиля мышления
  </div>
</template>

<style lang="scss">
  .question__title--big {
    font-size: 23px;
    line-height: 30px;
  }

  .loader {
    display: inline-block;
    position: relative;
    width: 80px;
    height: 80px;
  }
  .loader div {
    position: absolute;
    width: 6px;
    height: 6px;
    background: #3BDE7C;
    border-radius: 50%;
    animation: loader 1.2s linear infinite;
  }
  .loader div:nth-child(1) {
    animation-delay: 0s;
    top: 37px;
    left: 66px;
  }
  .loader div:nth-child(2) {
    animation-delay: -0.1s;
    top: 22px;
    left: 62px;
  }
  .loader div:nth-child(3) {
    animation-delay: -0.2s;
    top: 11px;
    left: 52px;
  }
  .loader div:nth-child(4) {
    animation-delay: -0.3s;
    top: 7px;
    left: 37px;
  }
  .loader div:nth-child(5) {
    animation-delay: -0.4s;
    top: 11px;
    left: 22px;
  }
  .loader div:nth-child(6) {
    animation-delay: -0.5s;
    top: 22px;
    left: 11px;
  }
  .loader div:nth-child(7) {
    animation-delay: -0.6s;
    top: 37px;
    left: 7px;
  }
  .loader div:nth-child(8) {
    animation-delay: -0.7s;
    top: 52px;
    left: 11px;
  }
  .loader div:nth-child(9) {
    animation-delay: -0.8s;
    top: 62px;
    left: 22px;
  }
  .loader div:nth-child(10) {
    animation-delay: -0.9s;
    top: 66px;
    left: 37px;
  }
  .loader div:nth-child(11) {
    animation-delay: -1s;
    top: 62px;
    left: 52px;
  }
  .loader div:nth-child(12) {
    animation-delay: -1.1s;
    top: 52px;
    left: 62px;
  }
  @keyframes loader {
    0%, 20%, 80%, 100% {
      transform: scale(0.5);
    }
    50% {
      transform: scale(2);
    }
  }

  .loading-dots {
    font-family: 'PT Serif';
    font-weight: 400;
    font-size: 14px;
    line-height: 19px;
    letter-spacing: 0.05em;
    margin-bottom: 250px;
    color: #FFFFFF;
  }

  .loading-dots::after {
    content: '';
    animation: dots 2s infinite;
  }

  @keyframes dots {
    0% {
      content: "";
    }
    10% {
      content: ".";
    }
    20% {
      content: "..";
    }
    30% {
      content: "...";
    }
    40% {
      content: "....";
    }
    50% {
      content: ".....";
    }
    60% {
      content: "......";
    }
    70% {
      content: ".......";
    }
    80% {
      content: "........";
    }
    90% {
      content: ".........";
    }
    100% {
      content: "..........";
    }
  }
</style>