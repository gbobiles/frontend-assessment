<template>
  <div class="relative w-full h-auto">
    <img
      :src="bannerImage"
      alt="main-banner"
      class="w-full h-auto object-cover"
    />
    <div
      class="absolute inset-0 flex flex-col justify-center items-center text-center text-white p-10"
    >
      <h2 class="text-4xl font-bold">Hello Developer!</h2>
      <p class="text-lg mt-2">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "main-banner",
  data() {
    return {
      bannerImage: "",
    };
  },
  mounted() {
    this.updateBannerImage();
    window.addEventListener("resize", this.updateBannerImage);
  },
  beforeMount() {
    window.removeEventListener("resize", this.updateBannerImage);
  },
  methods: {
    updateBannerImage() {
      if (window.innerWidth <= 767) {
        this.bannerImage = "https://via.placeholder.com/600x600";
      } else {
        this.bannerImage = "https://via.placeholder.com/1920x650";
      }
    },
  },
};
</script>
