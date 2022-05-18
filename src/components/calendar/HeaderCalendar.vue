<template>
  <v-app-bar>
    <v-spacer></v-spacer>
    <v-btn
      @click="prev"
      class="mx-2"
      fab
      dark
      small
      color="primary"
    >
      <v-icon dark>
        mdi-chevron-left
      </v-icon>
    </v-btn>

    <v-btn
      @click="today"
      class="ma-2"
      outlined
      color="indigo"
    >
      Today
    </v-btn>

    <v-btn
      @click="next"
      class="mx-2"
      fab
      dark
      small
      color="primary"
    >
      <v-icon dark>
        mdi-chevron-right
      </v-icon>
    </v-btn>
  </v-app-bar>
</template>

<script>
export default {
  name: 'HeaderCalendar',

  methods: {
    prev () {
      this.$emit('prev-month')
    },

    today () {
      this.$emit('today')
    },

    next () {
      this.$emit('next-month')
    }
  }
}
</script>

<style></style>
