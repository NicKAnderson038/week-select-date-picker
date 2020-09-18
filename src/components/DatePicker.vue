<template>
  <div id="app">
  <v-app id="inspire">
    <v-row justify="center">
      <div>
        <br>
        <div class="subheading">Click on a Monday Date to select the week</div>
        <v-date-picker
          v-model="date0"
          :allowed-dates="allowedDates"
          :events="functionEvents"
        ></v-date-picker>
      </div>
    </v-row>
  </v-app>
</div>
</template>

<script>
import moment from 'moment';
  export default {
    name: 'DatePicker',
    data: () => ({
    date0: new Date().toISOString().substr(0, 10),
    dates: ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday'],
    selectableDate: 'Monday'
  }),
  methods: {
    validateMonday (date, skip) {
      const now = moment(date).format('dddd')
      if (now == this.selectableDate) return skip ? true : ['red', '#00f']
      if (now == 'Monday') return skip ? false: true
      if (now == 'Tuesday') return skip ? false: true
      if (now == 'Wednesday') return skip ? false: true
      if (now == 'Thursday') return skip ? false: true
      if (now == 'Friday') return skip ? false: true
      return false
    },
    allowedDates (date) {
      return this.validateMonday(date, true)
    },
    functionEvents (date) {
      return this.validateMonday(date)
    }
  },
  }
</script>
