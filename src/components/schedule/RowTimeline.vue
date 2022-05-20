<template>
  <div>
    <v-row class="wrapper">
      <div
        @mousemove="onMouseMove"
        class="timeline-row"
        ref="timeline"
      >
        <div
          v-for="assignment in user.assignments"
          :key="assignment.id"
          @mousedown.prevent="onMouseDown"
          @click="onClick"
          class="assigment"
          ref="task"
          :style="styleObject"
        >
          <ui-resizable
            :width="width"
            @update-width="updateWidth"
          />
        </div>
      </div>
    </v-row>
    {{ width }}
  </div>
</template>

<script>
import UiResizable from '@/components/ui/UiResizable'
export default {
  name: 'RowTimeline',

  components: { UiResizable },

  props: {
    user: {
      type: Object,
      required: false
    }
  },

  data () {
    return {
      styleObject: {
        left: 0
      },
      width: 0
    }
  },

  methods: {
    onMouseDown (event) {
      const timeline = this.$refs.timeline
      const task = this.$refs.task

      task.forEach(task => {
        const shiftX = event.clientX - task.getBoundingClientRect().left
        document.addEventListener('mousemove', onMouseMove)
        document.addEventListener('mouseup', onMouseUp)
        // console.log('TASK', typeof task)

        function onMouseMove (event) {
          const newLeft = event.clientX - shiftX - timeline.getBoundingClientRect().left

          const coord = newLeft % 50 ? 0 : newLeft

          if (coord !== 0) {
            task.style.left = (coord - 2) + 'px'
          }
        }

        function onMouseUp () {
          document.removeEventListener('mouseup', onMouseUp)
          document.removeEventListener('mousemove', onMouseMove)
        }
      })
    },

    onMouseMove (event) {
      const coord = event.pageX
      this.test = coord % 10 ? 0 : coord
      // console.log(this.test)
    },

    onClick () {
      console.log('click!!!')
    },

    updateWidth (width) {
      console.log('ccccc')
      const task = this.$refs.task
      task.style.width = width
    }
  },

  mounted () {
    this.$refs.task.forEach(elem => {
      console.log(elem.clientWidth)
      this.width = elem.clientWidth
    })
  }
}
</script>

<style scoped>

.wrapper {
  padding-top: 20px;
}
.timeline-row {
  position: relative;
  /* border: 2px solid #e0e0e0; */
  width: 100%;
  height: 40px;
}

.assigment {
  position: absolute;
  width: 200px;
  height: 32px;
  border-radius: 10px;
  background: orange;
  display: flex;
  justify-content: flex-end;
  align-items: stretch;
  /* margin-left: 44px; */
}

.resizable {
  width: 8px;
}
</style>
