<template>
  <div>
    <v-calendar-weekly
    :start="firstday"
  />
  <!-- <v-row>
    <v-col v-for="day in 7" :key="day">
      <v-card-text> {{ day }} </v-card-text>
    </v-col>
  </v-row> -->
  {{ getFirstDayOfWeek() }}
  </div>
</template>

<script>
export default {
  data () {
    return {
      date: new Date(),
      firstday: '2022-9-4',
      diff: 0
    }
  },

  methods: {
    // getFirstday () {
    //   const firstDay = new Date(this.date.setDate(this.date.getDate() - this.date.getDay())).toUTCString()
    //   console.log(firstDay)
    // },

    getFirstDayOfWeek () {
      const day = this.date.getDay()

      // console.log(day)

      this.diff = this.date.getDate() - day + (day === 0 ? -6 : 1)

      this.firstday = `${this.date.getFullYear()}-${this.date.getMonth() + 1}-${this.diff}`
      console.log(`${this.date.getFullYear()}-${this.date.getMonth() + 1}-${this.diff}`)

      console.log(new Date(this.date.setDate(this.diff)))
    }
  },

  computed: {}
}
</script>
