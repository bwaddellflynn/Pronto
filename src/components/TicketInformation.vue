<template>
  <div class="data-container bg-white shadow rounded-lg">
    <div class="p-4">
      <!-- Table Header -->
      <div class="grid grid-cols-7 gap-4 font-bold py-2">
        <div class="col-span-1">Ticket Number</div>
        <div class="col-span-2">Title</div>
        <div class="col-span-4">Description</div>
      </div>
      <!-- Table Body -->
      <div class="divide-y divide-gray-200">
        <div v-for="ticket in tickets" :key="ticket.id" class="grid grid-cols-7 gap-4 py-2">
          <div class="col-span-1">{{ ticket.number }} <br>In Progress</div>
          <div class="col-span-2">{{ ticket.title }}</div>
          <div class="col-span-4">{{ ticket.description }}</div>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
import { faker } from '@faker-js/faker';

export default {
  name: 'TicketInformation',
  data() {
    return {
      tickets: this.generateTickets(10) // Generate 10 IT ticket objects
    };
  },
  methods: {
    // Placeholder data generated with Faker
    generateTickets(count) {
      const tickets = [];
      for (let i = 0; i < count; i++) {
        tickets.push({
          id: i,
          number: faker.random.alphaNumeric(6).toUpperCase(),
          description: faker.hacker.phrase(),
          title: faker.git.commitMessage()
        });
      }
      return tickets;
    }
  }
};
</script>