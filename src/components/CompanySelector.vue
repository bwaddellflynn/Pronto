<template>
  <div class="flex p-5 items-center bg-transparent">
    <!-- Right side: Dropdowns and Submit button -->
    <div class="px-4 w-3/5"> <!-- First dropdown takes more space -->
      <p>Dedicated Service Agreements</p>
      <select class="w-full shadow form-select appearance-none
                    block px-3 py-1.5 text-base font-normal
                    text-gray-700 bg-white bg-clip-padding bg-no-repeat
                    border border-solid border-gray-300 rounded transition
                    ease-in-out m-0 focus:text-gray-700 focus:bg-white
                    focus:border-blue-600 focus:outline-none"
              v-model="selectedCompany">
          <option selected disabled>Select Company</option>
          <option v-for="company in companies" :key="company.id" :value="company.id">
            {{ company.name }}
          </option>
      </select>
    </div>
    <div class="px-5 w-1/5"> <!-- Second dropdown does not grow -->
      <p>Report Frequency</p>
      <select class="w-full shadow form-select appearance-none
                    block w-36 px-3 py-1.5 text-base font-normal
                    text-gray-700 bg-white bg-clip-padding bg-no-repeat
                    border border-solid border-gray-300 rounded transition
                    ease-in-out m-0 focus:text-gray-700 focus:bg-white
                    focus:border-blue-600 focus:outline-none"
              v-model="reportFrequency">
          <option selected disabled>Select Frequency</option>
          <option v-for="frequency in frequencies" :key="frequency.id" :value="frequency.value">
            {{ frequency.label }}
          </option>
      </select>
    </div>

    <div class="px-5 w-1/5"> <!-- Button does not grow -->
      <p>Update Frequency</p>
      <button class="w-full shadow px-4 py-2 bg-gray-500 text-white rounded hover:bg-cyan-500 transition-colors"
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
      selectedCompany: null,
      reportFrequency: null,
      companies: [
        { id: 5, value: 'ASCM', name: 'ASCM - Association for Supply Chain Management' },
        { id: 7, value: 'CARNA', name: 'CARNA - College & Association of Registered Nurses of Alberta' },
        { id: 3, value: 'AANA', name: 'AANA - American Association of Nurse Anesthetists' },
      ], // Holds fetched companies
      frequencies: [ 
        { id: 'bi-weekly', value: 'bi-weekly', label: 'Bi-weekly' },
        { id: 'monthly', value: 'monthly', label: 'Monthly' },
        { id: 'quarterly', value: 'quarterly', label: 'Quarterly' },
        // Add or remove frequencies as needed  
      ],
    };
  },

// TODO - Add logic to transform data retrieved from Pronto.API(Accelo service)
/*   mounted() {
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
  } */
};
</script>