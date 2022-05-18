<template>
  <div>
    <v-row class="wrapper">
      <div class="timeline-row" ref="timeline">
        <div
          @mousedown.prevent="onMouseDown"
          class="assigment"
          ref="task"
          :style="styleObject"
        >
        <span class="resizable">l</span>
        <span class="resizable" @mousedown="pullRight">r</span>
        </div>
      </div>
    </v-row>
  </div>
</template>

<script>
export default {
  name: 'RowTimeline',

  data () {
    return {
      styleObject: {
        left: 0
      },
      test: 0
    }
  },

  methods: {

    onMouseDown (event) {
      const timeline = this.$refs.timeline
      const task = this.$refs.task

      const shiftX = event.clientX - task.getBoundingClientRect().left

      document.addEventListener('mousemove', onMouseMove)
      document.addEventListener('mouseup', onMouseUp)

      function onMouseMove (event) {
        const newLeft = event.clientX - shiftX - timeline.getBoundingClientRect().left

        this.test = newLeft
        console.log('test', this.test)
        if (event.movementX > 0) {
          // m
          // const newLeft = event.clientX - shiftX
          for (let i = newLeft; i <= newLeft + 48; i++) {}
          console.log(newLeft)
        } else if (event.movementX < 0) {
          // n
        }

        // task.style.left = newLeft + 'px'
      }

      console.log('test 2', this.test)

      function onMouseUp () {
        document.removeEventListener('mouseup', onMouseUp)
        document.removeEventListener('mousemove', onMouseMove)
      }
    },

    pullRight () {
      console.log('pull')
    }
  }
}
</script>

<style scoped>
.wrapper {
  padding-top: 20px;
}
.timeline-row {
  position: relative;
  border: 2px solid #e0e0e0;
  width: 100%;
  height: 40px;
}

.assigment {
  position: absolute;
  width: 155px;
  height: 32px;
  border-radius: 10px;
  background: orange;
  display: flex;
  justify-content: space-between;
  align-items: stretch;
  margin-left: 44px;
}

.resizable {
  width: 8px;
}
</style>
