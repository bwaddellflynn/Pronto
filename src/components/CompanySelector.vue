<template>
    <div class="flex justify-between items-center p-4 bg-white">
      <!-- Left side: User info and navigation -->
      <div>...</div>
  
      <!-- Right side: Dropdowns and Submit button -->
      <div class="flex space-x-2">
        <select class="form-select appearance-none
                        block w-full px-3 py-1.5 text-base font-normal
                        text-gray-700 bg-white bg-clip-padding bg-no-repeat
                        border border-solid border-gray-300 rounded transition
                        ease-in-out m-0 focus:text-gray-700 focus:bg-white
                        focus:border-blue-600 focus:outline-none" v-model="selectedCompany">
          <option v-for="company in companies" :key="company.id" :value="company.id">
            {{ company.name }}
          </option>
        </select>
  
        <select class="form-select appearance-none
                        block w-full px-3 py-1.5 text-base font-normal
                        text-gray-700 bg-white bg-clip-padding bg-no-repeat
                        border border-solid border-gray-300 rounded transition
                        ease-in-out m-0 focus:text-gray-700 focus:bg-white
                        focus:border-blue-600 focus:outline-none" v-model="reportFrequency">
          <option v-for="frequency in frequencies" :key="frequency.id" :value="frequency.value">
            {{ frequency.label }}
          </option>
        </select>
  
        <button class="px-4 py-2 bg-blue-500 text-white font-bold rounded hover:bg-blue-700 transition-colors"
                @click="submit">
          SUBMIT
        </button>
      </div>
    </div>
  </template>

<script>
import AcceloService from '@/services/AcceloService'; // Update the import path as necessary

export default {
  data() {
    return {
      selectedCompany: null,
      reportFrequency: null,
      companies: [], // Holds fetched companies
      frequencies: [ 
        { id: 'bi-weekly', value: 'bi-weekly', label: 'Bi-weekly' },
        { id: 'monthly', value: 'monthly', label: 'Monthly' },
        { id: 'quarterly', value: 'quarterly', label: 'Quarterly' },
        // Add or remove frequencies as needed  
      ],
    };
  },
  mounted() {
    this.fetchCompanies();
  },
  methods: {
    // Fetch companies from the Accelo API
    async fetchCompanies() {
      try {
        const response = await AcceloService.getData('perbyte.accelo.com/endpoint');
        this.companies = response; // Update with the actual response structure
      } catch (error) {
        console.error('Error fetching companies:', error);
      }
    },
    // Handle the submit button click
    submit() {
      // TODO handle the submission of the selected values updating the report frequency
      console.log('Selected Company ID:', this.selectedCompany);
      console.log('Selected Report Frequency:', this.reportFrequency);
    }
  }
};
</script>