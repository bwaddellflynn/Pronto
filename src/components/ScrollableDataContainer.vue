<template>
  <div class="data-container max-h-96 overflow-auto bg-white shadow rounded-lg">
    <TicketInformation/>
  </div>
</template>

<script>
import TicketInformation from './TicketInformation.vue';

export default {
  name: 'ScrollableDataContainer',
  components: {
    TicketInformation,
}
}
</script>