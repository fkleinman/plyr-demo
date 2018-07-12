<template>
  <div id="app">
     <div>Duration: {{ duration }}</div>
        <plyr @ended="endedFunc" @timeupdate="videoTimeUpdated" @exitfullscreen="exitfullscreenFunc" :emit="['timeupdate', 'exitfullscreen','ended']" ref="player">
          <video>
              <source src="https://cdn.plyr.io/static/demo/View_From_A_Blue_Moon_Trailer-576p.mp4" type="video/mp4" />
          </video>
      </plyr>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      duration: null,
      player: null
    };
  },
  components: {},
  mounted() {
    this.player = this.$refs.player.player;
  },
  methods: {
    videoTimeUpdated: function(event) {
      this.duration = this.player.currentTime;
    },
    exitfullscreenFunc: function(event) {
      alert("sale del fullScreen");
    },
    endedFunc: function(event) {
      alert("TERMINO");
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
