<template>
  <div>
    <div class="text-center font-bold my-4">
      Selected Date Range: {{ displayDateRange }}
    </div>
    <DatePicker
      class="m-5"
      v-model="date"
      :attributes="attrs"
      :model-config="modelConfig"
      is-inline
      @input="updateDateRange"
    />
  </div>
</template>

<script>
import { DatePicker } from 'v-calendar';
import 'v-calendar/style.css';

export default {
  components: {
    DatePicker,
  },
  data() {
    return {
      date: null,
      attrs: [],
      modelConfig: {
        type: 'single', // or 'range' if you want to select a range of dates
        isRange: false, // true if you are using type 'range'
      },
    };
  },
  computed: {
    // Display the date range as a string
    displayDateRange() {
      if (!this.date) return 'None';
      // If you're using a range, adjust this to format the start and end dates
      return this.date.toLocaleDateString();
    },
  },
  methods: {
    updateDateRange(selectedDate) {
      // Update the date range attributes to highlight the range
      this.date = selectedDate;
      const start = new Date(selectedDate);
      const end = new Date(start);
      // Set end to 14 days ahead for bi-weekly, adjust accordingly for other ranges
      end.setDate(start.getDate() + 13);

      this.attrs = [
        {
          // Highlight the range with custom styling
          key: 'range',
          highlight: {
            backgroundColor: '#ffecb3', // Use a mild color for the highlight
          },
          dates: {
            start: start,
            end: end,
          },
        },
      ];
    },
  },
}
</script>
