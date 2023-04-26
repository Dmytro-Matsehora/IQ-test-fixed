<script>
  export default {
    data() {
      return {
        time: 600000,
      };
    },
    computed: {
      formatTime() {
        let minutes = Math.floor(this.time / 60000);
        let seconds = ((this.time % 60000) / 1000).toFixed(0);
        return `${minutes}:${(seconds < 10 ? "0" : "")}${seconds}`;
      },
    },
    mounted() {
      this.interval = setInterval(() => {
        this.time -= 1000;
        if (this.time <= 0) {
          clearInterval(this.interval);
        }
      }, 1000);
    },
    beforeDestroy() {
      clearInterval(this.interval);
    },
  };
</script>

<template>
  {{ formatTime }}
</template>
