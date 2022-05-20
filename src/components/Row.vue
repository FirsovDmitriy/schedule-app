<template>
  <div class="elem-row">
    <div class="wrapper" v-for="user in users" :key="user.id">
      <div class="wrapper__row" v-for="row in 6" :key="row">
        <div
          v-for="col in 7"
          :key="col"
          @click="addAssignment"
          class="col"
        >
        </div>
      </div>
      <row-timeline
        :user="user"
        class="row-timeline"
      />
    </div>
  </div>
</template>

<script>
import RowTimeline from './schedule/RowTimeline.vue'
export default {
  components: { RowTimeline },
  name: 'Row',

  data () {
    return {
      users: [
        {
          id: 1,
          title: 'user-1',
          assignments: [{
            id: 1,
            coordX: 0
          },
          {
            id: 2,
            coordX: 0
          }]
        },
        {
          id: 2,
          title: 'user-2',
          assignments: [{
            id: 2,
            coordX: 0
          }]
        },
        {
          id: 3,
          title: 'user-2'
        }
      ]
    }
  },

  methods: {
    addAssignment () {
      console.log('click')
    }
  }
}
</script>

<style scoped>
.elem-row {
  overflow-x: auto;
}
.wrapper {
  display: flex;
  height: 50px;
}

.wrapper__row {
  position: relative;
  height: 100%;
  display: grid;
  grid-template-columns: repeat(7, 50px);
}

.col {
  border: 1px solid navy;
  /* border-right: 1px solid navy; */
  transition: background .2s;
}

.col:hover {
  background: #f0f0f0;
  cursor: cell;
}

.task {
  position: absolute;
  width: 50px;
  height: 30px;
  background: darkmagenta;
  top: calc(50% - 15px);
}
</style>

<style scoped>
.row-timeline {
  position: absolute;
  width: 100%;
}
</style>
