<template>
  <div class="min-h-screen flex flex-col">
    <!-- Navbar -->
    <nav class="bg-gray-800 text-white p-4">
      <div class="container mx-auto flex justify-between items-center">
        <a href="#"><img class="object-scale-down h-7" alt="Vue logo" src="../assets/logo.png"></a>
        <div>
          <a href="#" class="mx-2 hover:text-gray-300 pr-4 pl-4">Home</a>
          <a href="#" class="mx-2 hover:text-gray-300 pr-4 pl-4">Help</a>
          <a href="#" class="mx-2 hover:text-gray-300 pr-4 pl-4">Logout</a>
        </div>
      </div>
    </nav>

    <!-- Main content -->
    <div class="flex flex-grow">
      <!-- Sidebar -->
      <aside class="w-80 bg-gray-100 pt-6">
        <div class="mb-9 mt-5">
          <img src="../assets/perbyte_logo.png" alt="User avatar" class="mx-auto rounded-full w-24 h-24 mb-2">
          <div class="text-center mt-5">
            <!-- TODO: Replace with values for username + email retrieved dynamically-->
            <p class="text-lg font-semibold">Jane Doe</p>
            <p> jane.doe@perbyte.com </p>
          </div>
        </div>

        <button class="w-full pt-2 pb-2 hover:bg-gray-300">Generate Report</button>
        <button class="w-full pt-2 pb-2 hover:bg-gray-300">View Last Report</button>
        <button class="w-full pt-2 pb-2 hover:bg-gray-300">Send Report</button>
        <button class="w-full pt-2 pb-2 hover:bg-gray-300">Preferences</button>
      </aside>

      <!-- Data display area -->
      <main class="flex-grow bg-white p-4">
        <!-- Your data will be displayed here -->
      </main>
    </div>

    <!-- Footer -->
    <footer class="bg-gray-200 p-4">
      <div class="container mx-auto text-center">
        <a href="#" class="mx-2 hover:text-gray-500">Terms of Service</a>
        <a href="#" class="mx-2 hover:text-gray-500">Privacy Policy</a>
        <a href="#" class="mx-2 hover:text-gray-500">Feedback</a>
      </div>
    </footer>
  </div>
</template>
