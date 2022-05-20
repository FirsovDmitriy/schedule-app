<template>
  <div>
    <!-- <v-calendar-weekly
      :start="startWeek"
    /> -->
    <div class="row-day">
      <div v-for="day in days" :key="day.format('YYYMMDD')">
        <div class="day">
          <span
            :class="{
              active: isCurrentDay(day)
            }"
          >
            {{ day.format('D') }}
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import moment from 'moment'

export default {
  props: {
    days: {
      type: Array,
      required: true
    },
    today: {
      type: Boolean
    }
  },

  data () {
    return {
      date: new Date(),
      thisDay: false
    }
  },

  methods: {
    isCurrentDay (day) {
      // this.$emit('is-current-day', day)
      return moment().isSame(day, 'd')
    }
  },

  mounted () {}
}
</script>

<style scoped>
.day {
  display: flex;
  justify-content: center;
  border-right: 2px solid #e0e0e0;
  border-bottom: 1px solid #e0e0e0;
  width: 50px;
}

.active {
  background: greenyellow;
}

.row-day {
  display: flex;
  flex-wrap: nowrap;
  flex: 1 1 auto;
  margin: -12px;
}
</style>
