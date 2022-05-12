<template>
  <div>
    <!-- <v-calendar-weekly
      :start="startWeek"
    /> -->
    <v-row>
      <v-col v-for="day in days" :key="day">
        <div class="day">
          <span> {{ day }} </span>
        </div>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  props: {
    days: {
      type: Array,
      required: true
    }
  },

  data () {
    return {
      date: new Date()
    }
  },

  computed: {}
}
</script>

<style scoped>
.day {
  display: flex;
  justify-content: center;
  border-right: 1px solid #e0e0e0;
  border-bottom: 1px solid #e0e0e0;
}
</style>
