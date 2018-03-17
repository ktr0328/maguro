<template>
  <div id="maguro"><div>
</template>

<script>
import P5 from 'p5'

export default {
  name: 'maguro',
  data () {

  },
  methods: {
    sketch: function (p) {
      p.setup = () => p.createCanvas(document.body.clientWidth, document.body.clientHeight)

      p.draw = () => {
      }
    }
  },
  mounted: function () {

  }
}
</script>

<style>

</style>
