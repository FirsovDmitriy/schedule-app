<template>
  <v-app>
    <the-header />
    <v-main>
      <v-row>
        <v-col>
          <timeline-week
            :days="week()"
          />
        </v-col>
      </v-row>
      {{ nextWeek() }}
    </v-main>
  </v-app>
</template>

<script>
import TheHeader from '@/components/TheHeader'
// import TimelineWeek from '@/components/TimelineWeek'
import TimelineWeek from '@/components/calendar/TimelineWeek'
import moment from 'moment'

moment.updateLocale('en', { week: { dow: 1 } })

export default {
  name: 'App',

  components: {
    TheHeader, TimelineWeek
  },

  data () {
    return {
      startWeek: moment().startOf('week'),
      startWeekFormat: moment().startOf('week').format('YYYY-MM-DD'),
      endWeek: moment().endOf('week'),
      startMonth: moment().startOf('month').format('YYYY-MM-DD'),
      endMonth: moment().endOf('month').format('DD'),
      weeks: moment().weeksInYear(),
      daysWeek: []
    }
  },

  methods: {
    week () {
      const start = this.startWeek.format('DD')
      const end = this.endWeek.format('DD')
      const days = []

      for (let i = start; i <= end; i++) {
        days.push(i - 0)
      }

      return days
    },

    nextWeek () {
      // const week = this.startWeek
      // week.add(7, 'd')
      // console.log('start next week', week.format('YYYY-MM-DD'))
      // week.add(7, 'd')
      // console.log('start next week 2', week.format('YYYY-MM-DD'))
      // week.add(7, 'd')
      // console.log('start next week 3', week.format('YYYY-MM-DD'))
      // week.add(7, 'd')
      // console.log('start next week 4', week.format('YYYY-MM-DD'))
      // week.add(7, 'd')
      // console.log('start next week 5', week.format('YYYY-MM-DD'))
    }
  },

  computed: {
    renderWeek () {
      const calendar = []
      return calendar
    }
  },

  mounted () {
    console.log(typeof this.startWeek)
    // console.log('weekend', this.endWeek)
    console.log('end month', this.endMonth)
  }
}
</script>
