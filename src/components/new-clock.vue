<template>
  <div class="clock">
    <div>{{msg}}</div>
    <input class="inputStyle" type="text" v-model="textFromInput" placeholder="text"/>
    <input class="inputStyle" type="text" v-model="dateFromInput" placeholder="date"/>
    <button class="inputStyle" @click="clickHandler">ENTER</button>
  </div>
</template>

<script>
export default {
  name: 'Clock',
  data () {
    return {
      textFromInput: '',
      dateFromInput: '',
      msg: 'Enter you data'
    }
  },
  methods: {
    clickHandler (e) {
      this.$emit('change', this.textFromInput)
      this.textFromInput = ''
      this.dateFromInput = ''
    }
  }
}
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
