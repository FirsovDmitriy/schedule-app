<template>
  <v-app>
    <the-header />
    <v-main>
      <v-row>
        <v-col>
          <timeline-week />
        </v-col>
      </v-row>
    </v-main>
  </v-app>
</template>

<script>
import TheHeader from '@/components/TheHeader'
// import TimelineWeek from '@/components/TimelineWeek'
import TimelineWeek from '@/components/calendar/TimelineWeek'

export default {
  name: 'App',

  components: {
    TheHeader, TimelineWeek
  },

  data () {
    return {}
  }
}
</script>
