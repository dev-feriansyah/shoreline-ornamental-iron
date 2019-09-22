<template>
  <header class="container mx-auto md:flex md:items-center md:py-2">
    <div class="p-3 flex items-center justify-between">
      <a href="#">
        <img class="h-10 md:h-12" src="@/assets/logo.svg" alt="Sharoline logo" />
      </a>

      <button
        type="button"
        class="p-2 text-gray-800 hover:text-gray-600 focus:outline-none focus:text-gray-600 md:hidden"
        @click="isOpen = !isOpen"
        @key.space="isOpen = !isOpen"
      >
        <svg class="h-6 w-6 fill-current" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
          <path v-show="!isOpen"
            d="M4 5h16a1 1 0 0 1 0 2H4a1 1 0 1 1 0-2zm0 6h16a1 1 0 0 1 0 2H4a1 1 0 0 1 0-2zm0 6h16a1 1 0 0 1 0 2H4a1 1 0 0 1 0-2z"
          />
          <path v-show="isOpen" d="M17.803 15.042a1.959 1.959 0 0 1-2.761 2.761L9.5 12.261l-5.542 5.542a1.958 1.958 0 0 1-2.761-2.76L6.739 9.5 1.197 3.958a1.958 1.958 0 0 1 2.76-2.761L9.5 6.739l5.542-5.542a1.959 1.959 0 0 1 2.761 2.76L12.261 9.5l5.542 5.542z"/>
          
        </svg>
      </button>
    </div>
    <nav :class="{ hidden: !isOpen }" class="md:flex md:w-full md:pr-3">
      
      <div class="px-3 py-4 flex flex-col border-t-2 border-gray-400 md:border-0 md:flex-row">
        <a href="#" class="text-gray-800 hover:text-gray-500 focus:outline-none focus:text-gray-500">Products</a>
        <a href="#" class="mt-4 text-gray-800 hover:text-gray-500 focus:outline-none focus:text-gray-500 md:mt-0 md:ml-4">About</a>
        <a href="#" class="mt-4 text-gray-800 hover:text-gray-500 focus:outline-none focus:text-gray-500 md:mt-0 md:ml-4">Resources</a>
        <a href="#" class="mt-4 text-gray-800 hover:text-gray-500 focus:outline-none focus:text-gray-500 md:mt-0 md:ml-4">Contact Us</a>
      </div>
      
      <div class="md:hidden">
        <hr class="border-t-2 border-gray-400" />
        <div class="px-3 py-4">
          <div class="flex items-center">
            <img src="@/assets/avatar.jpg" alt="Avatar Face" class="w-8 h-8 object-cover rounded-full border border-gray-600" />
            <span class="ml-4 text-gray-800">Dwi Lestari</span>
          </div>
          <a href="#" class="mt-4 block text-gray-800 hover:text-gray-600 focus:outline-none focus:text-gray-600">Shopping Cart</a>
          <a href="#" class="mt-4 block text-gray-800 hover:text-gray-600 focus:outline-none focus:text-gray-600">Account Setting</a>
        </div>
      </div>

      <div class="hidden md:ml-auto md:flex md:items-center">
        <a href="#view-shop" class="h-12 w-12 bg-blue-100 hover:bg-blue-200 focus:outline-none focus:bg-blue-200 shadow-lg rounded-full flex items-center justify-center appearance-none">
          <svg
            class="h-6 w-6 fill-current text-blue-500"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
          >
            <path
                d="M17 16a3 3 0 1 1-2.83 2H9.83a3 3 0 1 1-5.62-.1A3 3 0 0 1 5 12V4H3a1 1 0 1 1 0-2h3a1 1 0 0 1 1 1v1h14a1 1 0 0 1 .9 1.45l-4 8a1 1 0 0 1-.9.55H5a1 1 0 0 0 0 2h12zM7 12h9.38l3-6H7v6zm0 8a1 1 0 1 0 0-2 1 1 0 0 0 0 2zm10 0a1 1 0 1 0 0-2 1 1 0 0 0 0 2z"
              />
          </svg>
        </a>

        <div class="relative">
          <button @click="dropdownOpen = !dropdownOpen" @key.space="dropdownOpen = !dropdownOpen" type="button" class="ml-6 appearance-none">
            <img src="@/assets/avatar.jpg" alt="Avatar Face" class="w-16 h-16 object-cover rounded-full border-2 border-gray-600" />
          </button>

          <div v-show="dropdownOpen" class="py-2 w-40 -mt-2 mr-2 absolute right-0 z-30 bg-white overflow-hidden rounded shadow-2xl">
            <a href="#" class="px-3 py-2 block text-gray-800 hover:bg-blue-500 hover:text-blue-100 focus:outline-none focus:bg-blue-500 focus:text-blue-100">Account Setting</a>
            <a href="#" class="px-3 py-2 block text-gray-800 hover:bg-blue-500 hover:text-blue-100 focus:outline-none focus:bg-blue-500 focus:text-blue-100">History</a>
            <a href="#" class="px-3 py-2 block text-gray-800 hover:bg-blue-500 hover:text-blue-100 focus:outline-none focus:bg-blue-500 focus:text-blue-100">Log Out</a>
          </div>

          <!-- close on click anywhere -->
          <button v-show="dropdownOpen" @click="dropdownOpen = false" class="hidden focus:outline-none md:block md:fixed md:inset-0 md:h-full md:w-full md:z-20">
          </button>

        </div>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  data() {
    return {
      isOpen: false,
      dropdownOpen: false
    }
  },
  mounted() {
    const onEscape = (e) => {
      if (!this.dropdownOpen || e.key !== 'Escape') {
        return
      }
      this.dropdownOpen = false;
    }

    document.addEventListener('keydown', onEscape);

    this.$on('hook:destroyed', () => {
      document.removeEventListener('keydown', onEscape);
    });
  }
};
</script>
