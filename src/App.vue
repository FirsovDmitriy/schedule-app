<template>
  <v-app>
    <the-header />
    <v-main>
      <header-calendar
        @next-month="nextMonth"
        @today="today"
        @prev-month="prevMonth"
      />
      <v-row>
        <v-col v-for="(week, index) in getDaysWeek()" :key="index" class="week">
          <timeline-week
            :days="week"
            :today="isCurrentDay()"
            @is-current-day="isCurrentDay"
          />
        </v-col>
      </v-row>
      <row-timeline />
    </v-main>
  </v-app>
</template>

<script>
import TheHeader from '@/components/TheHeader'
// import TimelineWeek from '@/components/TimelineWeek'
import TimelineWeek from '@/components/calendar/TimelineWeek'
import HeaderCalendar from '@/components/calendar/HeaderCalendar'
import RowTimeline from '@/components/schedule/RowTimeline'

import moment from 'moment'

moment.updateLocale('en', { week: { dow: 1 } })

export default {
  name: 'App',

  components: {
    TheHeader, TimelineWeek, HeaderCalendar, RowTimeline
  },

  data () {
    return {
      currentDay: false,
      startWeek: moment().startOf('week'),
      startWeekFormat: moment().startOf('week').format('YYYY-MM-DD'),
      endWeek: moment().endOf('week'),
      // start day
      startMonth: moment().startOf('month').startOf('week'),
      endMonth: moment().endOf('month'),
      daysWeek: [],
      weeks: null
    }
  },

  methods: {
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
    },

    prevMonth () {
      this.startMonth = this.startMonth.clone().subtract(1, 'w')
    },

    today () {
      this.startMonth = moment().startOf('month').startOf('week')
    },

    nextMonth () {
      // console.log('next month', this.startMonth.add(1, 'M'))
      this.startMonth = this.startMonth.clone().add(1, 'w')
    },

    getDaysWeek () {
      const day = this.startMonth.clone().subtract(7, 'd')
      const weeks = [...Array(6)].map(() => {
        const startWeek = day.add(7, 'd').clone().subtract(1, 'd')
        const month = [...Array(7)].map(() => startWeek.add(1, 'd').clone())
        return month
      })
      // console.log(weeks)
      return weeks
    },

    isCurrentDay (day) {
      // console.log(moment().isSame(day, 'd'))
      return moment().isSame(day, 'd')
    }
  },

  computed: {
    week () {
      const start = this.startWeek.format('DD')
      const end = this.endWeek.format('DD')
      const days = []

      for (let i = start; i <= end; i++) {
        days.push(i - 0)
      }

      return days
    }
  },

  mounted () {
    // console.log(typeof this.startWeek)
    // console.log('weekend', this.endWeek)
    // console.log('current', this.currentDay)
  }
}
</script>

<style scoped>
.week {
  border-right: 1px solid #000;
}
</style>
