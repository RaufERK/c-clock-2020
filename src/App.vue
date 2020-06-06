<template>
  <div id="app">
    <cosmicClock
      v-for="(item, index) in clockArray"
      :key="index"
      :name="item.name"
      :date="item.name"
      @delete="handleDeleteClock(index)"
    />
    <new-Clock @change="handlerNewClock($event)" />
  </div>
</template>

<script>
import cosmicClock from './components/cosmic-clock';
import newClock from './components/new-clock';
export default {
  name: 'App',
  components: {
    cosmicClock,
    newClock,
  },
  data() {
    return {
      clockArray: [],
    };
  },
  mounted() {
    const result = localStorage.getItem('c-clock');
    const parsedStorage = JSON.parse(result);
    this.clockArray = [...parsedStorage];
  },
  methods: {
    handleDeleteClock(itemIndex) {
      console.log('DELETE - INDEX ->', itemIndex);
      this.clockArray.splice(itemIndex, 1);
      this.updateStore();
    },
    handlerNewClock(e) {
      console.log(e);
      this.clockArray.push({
        name: e,
        date: new Date(),
      });
      this.updateStore();
    },
    updateStore() {
      localStorage.setItem('c-clock', JSON.stringify(this.clockArray));
    },
  },
};
</script>

<style>
body {
  background-color: darkblue;
}

#app {
  display: flex;
  flex-wrap: wrap;
}
</style>
