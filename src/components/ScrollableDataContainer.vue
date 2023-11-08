<template>
    <div class="data-container max-h-96 overflow-auto bg-white shadow rounded-lg p-4">
      <!-- TODO - Content/Components will be rendered here -->
      <!-- Placeholder Content START -->
      <div v-for="n in 20" :key="n" class="py-2">
        Item {{ n }} - She sells sea shells by the sea shore.
      </div>
      <!-- Placeholder Content END -->
    </div>
  </template>
  
  <script>
  export default {
    name: 'ScrollableDataContainer',
    // TODO - Define props and data
  };
  </script>