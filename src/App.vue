<template>
  <v-app>
    <the-header />
    <v-main>
      <timeline-week />
    </v-main>
  </v-app>
</template>

<script>
import TheHeader from '@/components/TheHeader'
import TimelineWeek from '@/components/TimelineWeek'

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
