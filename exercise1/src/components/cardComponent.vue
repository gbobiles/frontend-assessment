<template>
  <div class="card flex flex-col md:flex-row gap-6 p-4">
    <!-- Loop through the cards array -->
    <div
      v-for="(card, index) in cards"
      :key="index"
      class="card__container flex flex-1 flex-col bg-white rounded-lg overflow-hidden p-5 text-center"
    >
      <img
        :src="card.image"
        :alt="'Card Image ' + (index + 1)"
        class="card__image w-full h-auto object-cover rounded-lg"
      />
      <div class="card__body p-4 flex flex-col flex-1">
        <p class="text-gray-600 mb-4 flex-1">{{ card.text }}</p>
        <div class="mt-auto">
          <button
            class="bg-transparent text-black px-4 py-2 rounded-full border-2 border-solid border-black uppercase font-bold"
          >
            {{ card.buttonText }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import "../assets/custom.css";

export default {
  name: "cardComponent",
  data() {
    return {
      // Array of card data
      cards: [
        {
          image: "https://via.placeholder.com/400x300",
          text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.",
          buttonText: "Read More",
        },
        {
          image: "https://via.placeholder.com/400x300",
          text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
          buttonText: "Read More",
        },
        {
          image: "https://via.placeholder.com/400x300",
          text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco.",
          buttonText: "Read More",
        },
      ],
    };
  },
};
</script>
