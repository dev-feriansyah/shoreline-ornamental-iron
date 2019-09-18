<template>
  <div>
    <div class="mt-6 md:flex md:items-center">
      <div class="md:w-2/3">
        <h3 class="text-2xl font-heading font-semibold capitalize text-gray-800">{{product.name}}</h3>
        <p
          class="mt-4 text-gray-800"
        >{{ product.description }}</p>
        <a
          type="button"
          :href="product.viewUrl"
          class="mt-6 btn btn-blue hidden md:inline-block"
        >View All</a>
      </div>

      <div class="md:ml-4 md:w-1/3">
        <img
          class="mt-6 h-64 max-w-full rounded-lg shadow-lg mx-auto object-cover md:mt-0 md:h-72"
          :src="product.imgUrl"
          :alt="product.name"
        />
      </div>
    </div>

    <a
      type="button"
      :href="product.viewUrl"
      class="mt-6 block btn btn-blue md:hidden"
    >View All</a>
  </div>
</template>

<script>
export default {
  props: ['product']
}
</script>