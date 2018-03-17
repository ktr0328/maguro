<template>
  <div>
  </div>
</template>

<script>
import P5 from 'p5'

export default {
  name: 'maguro',
  data () {
    return {
      img: '',
      objects: [],
      config: {
        maguro: {
          num: 15,
          speed: 2
        }
      }
    }
  },
  methods: {
    sketch: function (p) {
      p.setup = () => p.createCanvas(document.body.clientWidth, document.body.clientHeight)
      p.preload = () => {
        this.img = p.loadImage('src/renderer/assets/maguro.png')
      }

      p.draw = () => {
        p.clear()
        p.noStroke()
        p.smooth()

        p.fill(0)
        p.imageMode(p.CENTER)
        this.objects.forEach(e => {
          e.x = e.x + e.speed
          if (e.x < 0 - this.img.width / 5 / 2) e.x = document.body.clientWidth + this.img.width / 5 / 2
          p.image(this.img, e.x, e.y, this.img.width / 5, this.img.height / 5)
        })
      }
    }
  },
  mounted: function () {
    this.objects = (() => {
      const objs = []
      for (let i = 0; i < this.config.maguro.num; i++) {
        const obj = {
          x: document.body.clientWidth * Math.random(),
          y: document.body.clientHeight * Math.random(),
          speed: -4 * Math.random() - 1
        }
        objs.push(obj)
      }
      return objs
    })()

    // eslint-disable-next-line no-new
    new P5(this.sketch)
  }
}
</script>

<style>

</style>
