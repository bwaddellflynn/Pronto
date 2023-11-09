<template>
  <div class="relative">
    <div class="data-container max-h-96 overflow-auto bg-white shadow rounded-lg">
      <TicketInformation/>
    </div>
    <!-- Button to open modal -->
    <div class="flex justify-center pt-2">
      <button @click="isModalOpen = true" class="px-4 py-2 bg-gray-500 text-white rounded hover:bg-cyan-500">
        View All Data
      </button>
    </div>

    <!-- Modal -->
    <div v-if="isModalOpen" class="fixed inset-0 bg-gray-500 bg-opacity-75 flex items-center justify-center p-4 z-50">
      <div class="bg-white p-6 overflow-auto rounded shadow-lg-h-screen w-full h-full">
        <h3 class="text-lg font-bold mb-4">All Ticket Data</h3>
        
        <!-- Modal content -->
        <div class="overflow-y-auto">
          <TicketInformation/>
        </div>

        <!-- Close button -->
        <div class="flex justify-center pt-2">
          <button @click="isModalOpen = false" class="mt-4 px-4 py-2 bg-red-500 text-white rounded hover:bg-red-700">
            Close
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TicketInformation from './TicketInformation.vue';

export default {
  name: 'ScrollableDataContainer',
    components: {
    TicketInformation,
    },
  data() {
    return {
      isModalOpen: false,
      // ... other data properties ...
    };
  },
  // ... other component options ...
};
</script>
