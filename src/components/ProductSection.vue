<template>
  <section class="bg-gray-100">
    <div class="px-3 py-12 container mx-auto">
      <div class="flex justify-between items-center">
        <h2 class="text-4xl font-bold font-heading text-gray-800">All Products</h2>

        <div class="flex xl:hidden">
          <button
            type="button"
            @click="prev"
            class="inline-block text-orange-600 border-2 border-orange-700 appearance-none hover:bg-orange-600 hover:text-gray-100 focus:outline-none focus:bg-orange-600 focus:text-gray-100"
          >
            <svg
              class="w-8 h-8 fill-current"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
            >
              <path
                d="M14.7 15.3a1 1 0 0 1-1.4 1.4l-4-4a1 1 0 0 1 0-1.4l4-4a1 1 0 0 1 1.4 1.4L11.42 12l3.3 3.3z"
              />
            </svg>
          </button>

          <button
            type="button"
            @click="next"
            class="ml-4 inline-block text-orange-600 border-2 border-orange-700 appearance-none hover:bg-orange-600 hover:text-gray-100 focus:outline-none focus:bg-orange-600 focus:text-gray-100"
          >
            <svg
              class="w-8 h-8 fill-current"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
            >
              <path
                d="M9.3 8.7a1 1 0 0 1 1.4-1.4l4 4a1 1 0 0 1 0 1.4l-4 4a1 1 0 0 1-1.4-1.4l3.29-3.3-3.3-3.3z"
              />
            </svg>
          </button>
        </div>

        <nav class="hidden xl:flex">
          <button
            @click="productIndex = 0"
            :class="{'font-bold text-orange-700': productIndex === 0 }"
            class="px-3 py-4 appearance-none text-gray-800 focus:outline-none focus:font-bold focus:text-orange-700 hover:font-bold hover:text-orange-700"
          >Angle Brackets</button>
          <button
            @click="productIndex = 1"
            :class="{'font-bold text-orange-700': productIndex === 1 }"
            class="px-3 py-4 ml-8 appearance-none text-gray-800 focus:outline-none focus:font-bold focus:text-orange-700 hover:font-bold hover:text-orange-700"
          >Candle Hondlers & Sconces</button>
          <button
            @click="productIndex = 2"
            :class="{'font-bold text-orange-700': productIndex === 2 }"
            class="px-3 py-4 ml-8 appearance-none text-gray-800 focus:outline-none focus:font-bold focus:text-orange-700 hover:font-bold hover:text-orange-700"
          >Cast Iron Crosses</button>
          <button
            @click="productIndex = 3"
            :class="{'font-bold text-orange-700': productIndex === 3 }"
            class="px-3 py-4 ml-8 appearance-none text-gray-800 focus:outline-none focus:font-bold focus:text-orange-700 hover:font-bold hover:text-orange-700"
          >Iron Wall Decor</button>
        </nav>
      </div>

      <ProductItem :product="products[productIndex]" />
    </div>
  </section>
</template>

<script>
import ProductItem from "@/components/ProductItem.vue";

export default {
  data() {
    return {
      productIndex: 0,
      products: [
        {
          name: "Angle Brackets",
          description:
            "Labore qui magna ex elit aliqua aliqua qui do exercitation amet. Ipsum esse sint ullamco et. Laborum est elit exercitation sunt ad est quis. Labore laborum exercitation anim dolore commodo ad nisi pariatur minim irure consectetur. Dolore sit reprehenderit officia in proident nulla labore.",
          imgUrl: "/img/angle-brackets.jpg",
          viewUrl: "#angle-brackets",
          item: [
            {
              name: "Standard Bracket",
              imgUrl: "/img/standard-bracket.jpg",
              price: 75
            },
            {
              name: "Leaf Bracket",
              imgUrl: "/img/leaf-bracket.jpg",
              price: 145
            }
          ]
        },
        {
          name: "Candle Hondlers & Sconces",
          description:
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean nec facilisis metus. Donec id laoreet nibh. Nulla eu nulla in augue scelerisque consectetur a eu est. Donec nec nisl augue. Nulla nec nibh arcu. Sed interdum et nibh sed consequat. In velit nisi, pretium ultrices aliquet vel, imperdiet id orci. Curabitur efficitur.",
          imgUrl: "/img/candle-holders.jpg",
          viewUrl: "#candle-hondlers",
          item: [
            {
              name: "Candle Sconce-Iron Hand Forged",
              imgUrl: "/img/candle-sconce.jpg",
              price: 85
            },
            {
              name: "Decorative Metal Wall",
              imgUrl: "/img/decorative-metal-wall.jpg",
              price: 95
            }
          ]
        },
        {
          name: "Cast Iron Crosses",
          description:
            "Nulla nec nibh arcu. Sed interdum et nibh sed consequat. In velit nisi, pretium ultrices aliquet vel, imperdiet id orci. Curabitur efficitur, quam lacinia auctor viverra, metus ex euismod nulla, quis interdum nulla ligula ac velit. Cras nec feugiat purus, quis lobortis turpis. Curabitur eget maximus ante, nec scelerisque tortor. Vestibulum aliquam tellus nisi, sed lobortis nisi sodales id. Etiam a tincidunt ipsum.",
          imgUrl: "/img/iron-cross.jpg",
          viewUrl: "#iron-crosses",
          item: [
            {
              name: "Standard Bracket",
              imgUrl: "/img/standard-bracket.jpg",
              price: 75
            },
            {
              name: "Leaf Bracket",
              imgUrl: "/img/leaf-bracket.jpg",
              price: 145
            }
          ]
        },
        {
          name: "Iron Wall Decor",
          description:
            "Curabitur eget maximus ante, nec scelerisque tortor. Vestibulum aliquam tellus nisi, sed lobortis nisi sodales id. Etiam a tincidunt ipsum. Aliquam imperdiet ex quis erat eleifend, eget pharetra ante ultricies. Interdum et malesuada fames ac ante ipsum primis in faucibus.",
          imgUrl: "/img/wall-decor.jpg",
          viewUrl: "#wall-decor",
          item: [
            {
              name: "Candle Sconce-Iron Hand Forged",
              imgUrl: "/img/candle-sconce.jpg",
              price: 85
            },
            {
              name: "Decorative Metal Wall",
              imgUrl: "/img/decorative-metal-wall.jpg",
              price: 95
            }
          ]
        }
      ]
    };
  },
  methods: {
    prev() {
      if (this.productIndex !== 0) {
        return this.productIndex--;
      }
      this.productIndex = this.products.length - 1;
    },
    next() {
      if (this.productIndex !== this.products.length - 1) {
        return this.productIndex++;
      }
      this.productIndex = 0;
    }
  },
  components: {
    ProductItem
  }
};
</script>