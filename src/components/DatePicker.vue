<template>
  <div id="app">
    <v-app id="inspire">
      <v-row justify="center">
        <div>
          <br />
          <div class="subheading">
            Click on a Monday Date to select the week
          </div>
          <v-date-picker
            class="custome-week-date-picker"
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
import moment from 'moment'
export default {
  name: 'DatePicker',
  data: () => ({
    date0: new Date().toISOString().substr(0, 10),
    selectableDate: 'Monday',
  }),
  methods: {
    validateMonday(date, skip) {
      const now = moment(date).format('dddd')
      if (now == this.selectableDate) return skip ? true : ['#00f']
      return false
    },
    allowedDates(date) {
      return this.validateMonday(date, true)
    },
    functionEvents(date) {
      return this.validateMonday(date)
    },
  },
}
</script>

<style>
/* Place code in application root (un-scoped) */
.custome-week-date-picker
  > .v-picker__body
  > div
  > div
  > table
  > tbody
  > tr
  > td
  > button.v-btn--active {
  background-color: #82b1ff;
  border-color: #82b1ff;
  width: 185px;
  position: initial;
  color: white;
}

.custome-week-date-picker
  > .v-picker__body
  > div
  > div
  > table
  > tbody
  > tr
  > td
  > button.v-btn--active
  > .v-btn__content {
  justify-content: flex-start;
  margin-left: 10px;
}
</style>
