<template>
  
     <div class="bg-white">
    <div class="max-w-2xl mx-auto py-16 px-4 sm:py-24 sm:px-6 lg:max-w-7xl lg:px-8">
      <div class="mt-6 grid grid-cols-1 gap-y-10 gap-x-6 sm:grid-cols-2 lg:grid-cols-4 xl:gap-x-8">
        <div v-for="product in products" :key="product.id" class="group relative">
          <div class="w-full min-h-80 bg-gray-200 aspect-w-1 aspect-h-1 rounded-md overflow-hidden group-hover:opacity-75 lg:h-80 lg:aspect-none">
            <img :src="product.image" :alt="product.image" class="w-full h-full object-center object-fill lg:w-full lg:h-full" />
          </div>
          <div class="mt-4 flex justify-between">
            <div>
              <h3 class="text-sm font-bold text-gray-700">
                <a :href="product.href">
                  <span aria-hidden="true" class="absolute inset-0" />
                  {{ product.name }}
                </a>
              </h3>
              <p class="mt-1 text-sm text-gray-500">{{ product.color }}</p>
            </div>
            <p class="text-sm font-medium text-gray-900">{{ product.price }} $</p>
          </div>
          <button class="mt-5 bg-gray-200
                hover:bg-purple-700
                text-gray-700
                font-bold
                text-sm
                py-2
                px-4
                rounded-md
                focus:outline-none focus:shadow-outline
                w-full">Add to bag</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import ProductCards from "../components/ProductCards.vue";
import Axios from "axios";
export default {
  name: "Home",
  components: {
    
  },
  data() {
    return {
      products: [],
    };
  },
  mounted() {
    Axios.get("http://localhost:3000/products")
      .then((response) => {
        this.products = response.data.products;
        console.log(this.products);
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>
