<template>
  <div id="app">
    <button @click="start">Start</button>
    <button @click="stop">Stop</button>
    <button @click="reset">Reset</button>
    <p>{{formattedElapsedTime}}</p>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      elapsedTime: 0,
      timer: undefined
    };
  },
  computed: {
    formattedElapsedTime() {
      const date = new Date(null);
      // console.log(date, 'date')
      date.setSeconds(this.elapsedTime / 1000);
      // console.log(date.setSeconds(this.elapsedTime / 1000), 'date.setSeconds(this.elapsedTime / 1000)')
      const utc = date.toUTCString();
      // console.log(utc, 'utc')
      // console.log(utc.indexOf(":"), 'indexOf(":")')
      // console.log(utc.substr(utc.indexOf(":") - 3, 8), 'utc.substr(utc.indexOf(":") - 2, 8)')
      return utc.substr(utc.indexOf(":") - 2, 8);
    },
    functionPromise () {
      let promise = new Promise((resolve, reject) => {
        resolve("hello")
        reject("hi")
      })
      promise.then(res => {
        if(res) {
          resolve
        }
      }).catch (error => {

      })
    }
  },
  methods: {
    start() {
      this.timer = setInterval(() => {
        this.elapsedTime += 1000;
      }, 1000);
    },
    stop() {
      clearInterval(this.timer);
    },
    reset() {
      this.elapsedTime = 0;
    }
  }
};
</script>