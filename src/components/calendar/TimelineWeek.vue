<template>
  <div>
    <!-- <v-calendar-weekly
      :start="startWeek"
    /> -->
    <v-row>
      <v-col v-for="day in days" :key="day.format('YYYMMDD')">
        <div class="day">
          <span
            :class="{
              active: today
            }"
          >
            {{ day.format('D') }} {{ isCurrentDay(day) }}
          </span>
        </div>
      </v-col>
      {{ today }}
    </v-row>
  </div>
</template>

<script>
// import moment from 'moment'

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
      this.$emit('is-current-day', day)
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
}

.active {
  background: greenyellow;
}
</style>
