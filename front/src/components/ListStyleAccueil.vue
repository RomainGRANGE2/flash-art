<template>
  <div class="sm:mt-32">
    <div class="flex justify-between items-center mb-8">
      <div>
        <h4 class="font-bold" style="font-size: calc(1.325rem + 0.9vw)">
          Trouvez votre style
        </h4>
        <p class="text-xl">Découvrez toutes nos inspirations de tatouages</p>
      </div>

    </div>
    <div
      class="grid grid-cols-2 sm:grid-cols-4 lg:grid-cols-6 gap-8 justify-around items-center"
    >
      <RouterLink
        v-for="style in styles"
        :key="style.name"
        :to="`/result?style=${style._id}`"
        class="relative rounded-lg shadow-lg overflow-hidden h-52 w-full capitalize"
      >
        <img
          :src="style.image || '/src/assets/img/card.jpg'"
          :alt="style.name"
          class="w-full h-full object-cover"
        />
        <div class="absolute bottom-0 left-0 w-full bg-white p-2 text-center">
          <h5 class="font-bold text-lg">{{ style.name }}</h5>
        </div>
      </RouterLink>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const styles = ref([]);
fetch("http://35.180.205.13:3000/api/styles")
  .then((res) => res.json())
  .then((data) => (styles.value = data));
</script>
