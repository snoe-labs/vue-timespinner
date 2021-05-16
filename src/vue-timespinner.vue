<script>
import { defineComponent } from 'vue';
import dayjs from 'dayjs';
import customParseFormat from 'dayjs/plugin/customParseFormat';

dayjs.extend(customParseFormat);

export default /*#__PURE__*/defineComponent({
  name: 'VueTimespinner',
  props: {
    'startTime': String,
    'interval': String,
  },
  data() {
    return {
      time: dayjs(this.startTime || '18:00', 'HH:mm'),
      options: {
          interval: this.interval || 15
      },
    };
  },
  computed: {
    formattedTime() {
      return this.time.format('HH:mm')
    },
  },
  methods: {
    increment() {
      this.time = this.time.add(this.options.interval, 'minutes')
    },
    decrement() {
      this.time = this.time.subtract(this.options.interval, 'minutes')
    }
  },
});
</script>

<template>
  <div class="vue-timespinner">
    <button v-on:click="decrement">-</button>
    <input type="text" v-bind:value="formattedTime" />
    <button v-on:click="increment">+</button>
  </div>
</template>

<style scoped>
  .vue-timespinner {
    display: block;
    width: 400px;
    margin: 25px auto;
    text-align: center;
    padding: 25px;
  }
  .vue-timespinner p {
    margin: 0 0 1em;
  }
</style>
