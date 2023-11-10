<template>
  <div class="p-4">
    <!-- Display selected date range -->
    <div class="flex" v-if="dateRange.start && dateRange.end">
      <p>Start: {{ dateRange.start.toLocaleDateString() }}-</p>
      <p>End: {{ dateRange.end.toLocaleDateString() }}</p>
    </div>

    <DatePicker
      is-range
      v-model="dateRange"
      mode="range"
    />
  </div>
</template>

<script>
import { ref, watch } from 'vue';
import 'v-calendar/dist/style.css';
import { DatePicker } from 'v-calendar';

export default {
  components: {
    DatePicker
  },
  setup() {
    const dateRange = ref({ start: null, end: null });

    // Watcher function to update the range when a date is selected
    watch(dateRange, (newValue) => {
      if (newValue.start) {
        const selectedDate = new Date(newValue.start);
        // Set start to the previous Monday
        const start = new Date(selectedDate.setDate(selectedDate.getDate() - selectedDate.getDay() + (selectedDate.getDay() === 0 ? -6 : 1)));
        // Set end to the following Sunday (14 days from the start date)
        const end = new Date(new Date(start).setDate(start.getDate() + 13));

        // Update the dateRange with the new values
        dateRange.value.start = start;
        dateRange.value.end = end;
      }
    });

    return {
      dateRange,
    };
  }
};
</script>

<style scoped>
</style>