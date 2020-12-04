<template lang="pug">
- 'use strict'
- const logs = 7
- const streaks = 10
- const sticks = 4
- const sparks = 8
- const flames = 7
.moon
  .stars
    .star1 +
    .star2 +
    .star3 +

.stage
  .inputs
    input#vol-control(type='range' min='0' max='100' style='' v-model="volume")
  .campfire
    .sparks
      each spark in Array(sparks)
        .spark
    .logs
      each log in Array(logs)
        .log
          each streak in Array(streaks)
            .streak
    .sticks
      each stick in Array(sticks)
        .stick
    .fire
      .fire__red
        each flame in Array(flames)
          .flame
      .fire__orange
        each flame in Array(flames)
          .flame
      .fire__yellow
        each flame in Array(flames - 2)
          .flame
      .fire__white
        each flame in Array(flames)
          .flame
  .about
    h1(style='margin-bottom: 0px;' href) Created by D Gaeta
    h2(style='margin-top: 0px;margin-bottom: 0px;') A School/Free-Time Project
    h2(style='margin-top: 0px;margin-bottom: 0px;') Langs Learned VueJS, Pug, Stylus, HTML/CSS/JS
</template>

<script>
// @ is an alias to /src
import fire from '../assets/fire.mp3'

export default {
  name: 'Home',
  components: {
  },
  data () {
    return {
      fire: new Audio(fire),
      volume: 50
    }
  },
  async created () {
    this.fire.addEventListener('loadeddata', () => {
      this.fire.loop = true;
      this.fire.volume = (this.volume / 100);
      this.fire.autoplay = true
      this.fire.play()
      console.log(this.fire.volume)
    })
  },
  methods: {
    SetVolume (value) {
      console.log(value)
    }
  },
  watch: {
    'volume' (value) {
      this.fire.volume = (value / 100);
    }
  }
}
</script>
