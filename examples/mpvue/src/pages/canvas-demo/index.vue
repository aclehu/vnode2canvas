<template>
  <canvas canvas-id="demo-canvas" :style="{width: width + 'px', height: height+'px'}"></canvas>
</template>

<script>

  export default {
    data () {
      return {
        width: 0,
        height: 0,
        text: 'hello'
      }
    },
    canvasOptions: function () {
      let device = wx.getSystemInfoSync()
      this.width = device.windowWidth
      this.height = device.windowHeight
      return {
        canvasId: 'demo-canvas',
        width: this.width,
        height: this.height
      }
    },
    mounted () {
      setTimeout(() => {
          this.text = 'mpvue'
      }, 1000)
    },
    renderCanvas (h) {
      let device = wx.getSystemInfoSync()
      this.width = device.windowWidth
      this.height = device.windowHeight
      return h('view', [
        h('image', {
          props: {
            src: 'https://pic.u51.com/sfs-gateway/api/v1/download/5f7dac8228354008ae6f69f67c1c0fa410d6'
          },
          style: {
            left: 10,
            top: 10,
            width: 100,
            height: 100,
            fill: '#000',
            fontSize: 18,
            radius: 20
          }
        }),
        h('text', {
          style: {
            left: 120,
            top: 10,
            fill: '#000',
            fontSize: 18,
            width: 150,
            ellipse: true
          }
        }, this.text)
      ])
    }
  }
</script>
