<script>
import { defineComponent } from 'vue';
import VueTimespinner from '@/vue-timespinner.vue';

export default defineComponent({
  name: 'ServeDev',
  components: {
    VueTimespinner
  }
});
</script>

<template>
  <div id="app">
    <vue-timespinner interval="15" startTime="16:15" />
  </div>
</template>
