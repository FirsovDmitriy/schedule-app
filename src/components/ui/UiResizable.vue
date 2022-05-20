<template>
  <div
    @mousedown="grab"
    @mouseup="onMouseUp"
    ref="resizable"
    class="ui-resizable"
  >
  l
  </div>
</template>

<script>
export default {
  name: 'UiResizable',

  props: {
    width: {
      type: Number,
      required: true
    }
  },

  data () {
    return {
      shiftX: 0
    }
  },

  methods: {
    grab (event) {
      console.log('mouse down')
      this.shiftX = event.clientX - this.$refs.resizable.getBoundingClientRect().left
      document.addEventListener('mousemove', this.stretchingTask)
    },

    onMouseUp () {
      console.log('mouse up')
    },

    stretchingTask (event) {
      // console.log('document client X', event.clientX)
      const resizable = this.$refs.resizable
      const newWidth = event.clientX - this.shiftX - resizable.getBoundingClientRect().left
      this.$emit('update-width', newWidth)
      console.log('new width', newWidth)
    },

    test (event) {
      console.log('clientX', event.clientX)
    }
  },

  mounted () {
    // document.addEventListener('mousemove', this.stretchingTask)
  }
}
</script>

<style>
.ui-resizable {
  display: flex;
  align-items: center;
  width: 8px;
}
</style>
