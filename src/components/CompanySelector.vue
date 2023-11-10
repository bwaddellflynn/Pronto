<template>
  <div class="flex pb-4 items-center bg-transparent">
    <!-- Right side: Dropdowns and Submit button -->
    <div class="px-4 w-3/5">
      <p>Dedicated Service Agreements</p>
      <select class="w-full shadow form-select appearance-none
                    block px-3 py-1.5 text-base font-normal
                    text-gray-700 bg-white bg-clip-padding bg-no-repeat
                    border border-solid border-gray-300 rounded transition
                    ease-in-out m-0 focus:text-gray-700 focus:bg-white
                    focus:border-cyan-600 focus:outline-none"
              v-model="selectedCompany">
          <option disabled value="">Select Company</option>
          <option v-for="company in companies" :key="company.id" :value="company.id">
            {{ company.name }}
          </option>
      </select>
    </div>

    <div class="px-5 w-1/5">
      <p>Report Frequency</p>
      <select class="w-full shadow form-select appearance-none
                    block px-3 py-1.5 text-base font-normal
                    text-gray-700 bg-white bg-clip-padding bg-no-repeat
                    border border-solid border-gray-300 rounded transition
                    ease-in-out m-0 focus:text-gray-700 focus:bg-white
                    focus:border-cyan-600 focus:outline-none"
              v-model="reportFrequency" @change="onFrequencyChange">
          <option disabled value="">Select Frequency</option>
          <option v-for="frequency in frequencies" :key="frequency.id" :value="frequency.value">
            {{ frequency.label }}
          </option>
      </select>
    </div>

    <div class="px-5 w-1/5">
      <p>Update Frequency</p>
      <button class="w-full shadow px-4 py-2 text-white rounded transition-colors"
              :class="{'bg-gray-500': isSubmitDisabled, 'bg-cyan-700 hover:bg-cyan-500': !isSubmitDisabled}"
              :disabled="isSubmitDisabled"
              @click="submit">
        SUBMIT
      </button>
    </div>
  </div>
</template>

<script>
//import AcceloService from '@/services/AcceloService'; // Update the import path as necessary

export default {
  data() {
    return {
      selectedCompany: '',
      reportFrequency: '',
      companies: [
        { id: 5, value: 'ASCM', name: 'ASCM - Association for Supply Chain Management' },
        { id: 7, value: 'CARNA', name: 'CARNA - College & Association of Registered Nurses of Alberta' },
        { id: 3, value: 'AANA', name: 'AANA - American Association of Nurse Anesthetists' },
      ],
      frequencies: [
        { id: 1, value: 'on-demand', label: 'On-Demand' },
        { id: 2, value: 'bi-weekly', label: 'Bi-weekly' },
        { id: 3, value: 'monthly', label: 'Monthly' },
        { id: 4, value: 'quarterly', label: 'Quarterly' },
        { id: 5, value: 'yearly', label: 'Yearly' },

      ],
      isSubmitDisabled: true, // Control the disabled state of the button
    };
  },
  methods: {
    onFrequencyChange() {
      this.isSubmitDisabled = !this.reportFrequency;
    },
    submit() {
      if (!this.isSubmitDisabled) {
        // TODO - Handle the submission logic here
        console.log('Selected Company ID:', this.selectedCompany);
        console.log('Selected Report Frequency:', this.reportFrequency);
      }
    },
    // TODO - Add fetchcompanies logic
  },
};
</script>
