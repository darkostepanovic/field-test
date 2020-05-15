<template>
  <div class="field">
    <div class="field__title">
      {{ name }}
    </div>
    <div class="field__content">
      <div class="field__value">
        {{ value }}
      </div>
      <div class="field__arrow" v-if="increase">
        +
      </div>
      <div class="field__arrow" v-else>
        -
      </div>
    </div>
    <button v-if="valueStart" v-on:click="stop()">Stop</button>
    <button v-else v-on:click="start()">Start</button>
  </div>
</template>

<script>
export default {
  name: "Field",
  props: {
    name: String
  },
  data() {
    return {
      value: 3,
      valueStart: true,
      interval: null,
      increase: true
    };
  },
  methods: {
    start() {
      this.interval = setInterval(() => {
        this.valueStart = true;
        let v = this.generateValue();
        const sign = this.generateValue();
        if (sign > 1.4) {
          this.increase = true;
        } else {
          v = v * -1;
          this.increase = false;
        }

        // TO-DO:  push to history array

        this.value = Math.round((this.value + v) * 10) / 10;
      }, 2000);
    },
    stop() {
      this.valueStart = false;
      clearInterval(this.interval);
    },
    generateValue() {
      return Math.round((Math.random() + 1) * 10) / 10;
    }
  },
  mounted() {

    // TO-DO: get last value

    this.start();
  },
  beforeDestroy() {
      this.stop();
  }
};
</script>
