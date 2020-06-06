<template>
  <div class="clock">
    <div>{{ name }}</div>
    <div>{{ dateFormated }}</div>
    <div><button @click="$emit('delete')">DELETE</button></div>
     <v-btn small>Normal</v-btn>
  </div>
</template>

<script>
import moment from 'moment';

export default {
  name: 'cosmicClock',
  props: {
    name: String,
    date: String,
  },
  data() {
    return {
      textFromInput: '1111',
      msg: 'Enter you data',
    };
  },
  computed: {
    dateFormated() {
      const dataString = this.data;
      return moment(dataString).format('DD-MM-YYYY');
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.clock {
  background-color: white;
  width: 100px;
  height: 100px;
  margin: 10px;
  padding: 10px;
  border-radius: 10px;
  border: solid 10px darkviolet;
}

.inputStyle {
  border-radius: 3px;
  border: solid 1px black;
  margin: 5px;
  width: 90%;
}
</style>
