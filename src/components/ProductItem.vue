<template>
  <div>
    <div class="mt-6 md:flex md:items-center">
      <div class="md:w-2/3 xl:w-1/3">
        <h3 class="text-2xl font-heading font-semibold capitalize text-gray-800">{{product.name}}</h3>
        <p class="mt-4 text-gray-800">{{ product.description }}</p>
        <a
          type="button"
          :href="product.viewUrl"
          class="mt-6 btn btn-blue hidden md:inline-block"
        >View All</a>
      </div>

      <div class="md:ml-4 md:w-1/3 xl:w-2/3 xl:flex">
        <div class="xl:flex">
          <img
            class="mt-6 h-64 max-w-sm mx-auto rounded-lg shadow-lg object-cover md:mt-0 md:h-72 xl:ml-24 xl:mr-0 xl:h-auto"
            :src="product.imgUrl"
            :alt="product.name"
          />
        </div>
        <div class="hidden xl:ml-6 xl:flex xl:flex-col">
          <figure class="appearance-none bg-white shadow rounded" v-for="(item,i) in product.item" :key="i" :class="{ 'mt-4': i > 0 }">
            <img :src="item.imgUrl" :alt="item.name" class="object-cover w-full h-40" />
            <figcaption class="p-4 border-t-2 border-gray-500">
              <span class="block font-bold text-gray-700">{{ item.name }}</span>
              <span class="mt-1 block text-gray-700">
                <span class="font-bold mr-1">$</span>{{ item.price | toUSD }}
              </span>
            </figcaption>
          </figure>
        </div>
      </div>
    </div>

    <a type="button" :href="product.viewUrl" class="mt-6 block btn btn-blue md:hidden">View All</a>
  </div>
</template>

<script>
export default {
  props: ["product"],
  filters: {
    toUSD(price) {
      const formatter = new Intl.NumberFormat('en-US', {
        style: 'currency',
        currency: 'USD',
      });

      return formatter.format(price).substring(1);
    }
  }
};
</script>