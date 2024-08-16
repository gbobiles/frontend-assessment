<template>
  <div class="data-table h-auto w-full">
    <!-- Tabs for Desktop -->
    <div
      class="data-table__tab h-auto mt-5 mx-auto p-4 rounded-lg bg-gradient-to-r from-blue-500 to-indigo-500 shadow-lg"
      v-show="isDesktop"
    >
      <div class="flex border-b border-indigo-700">
        <button
          v-for="(section, index) in sections"
          :key="index"
          :class="{
            'border-indigo-500 text-white bg-gradient-to-r from-green-400 to-blue-500':
              selectedTab === index,
            'text-indigo-100': selectedTab !== index,
          }"
          @click="selectTab(index)"
          class="px-4 py-2 -mb-px border-b-2 rounded-t-lg border-indigo-500"
        >
          {{ section.title }}
        </button>
      </div>
      <div class="p-4 bg-white rounded-b-lg shadow-lg">
        <div ref="tabContent" v-html="sections[selectedTab].content"></div>
      </div>
    </div>

    <!-- Accordion for Mobile -->
    <div class="data-table__accordion m-10" v-show="!isDesktop">
      <div v-for="(section, index) in sections" :key="index">
        <button
          @click="toggleAccordion(index)"
          class="w-full text-left p-4 bg-gradient-to-r from-green-400 to-blue-500 text-white shadow-md rounded-lg mb-2"
        >
          {{ section.title }}
        </button>
        <div
          v-if="activeAccordion === index"
          class="p-4 bg-white rounded-lg shadow-lg border-solid border-2 border-indigo-500 mb-2"
        >
          <div ref="accordionContent" v-html="section.content"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import sectionData from "../data.json";
import "../assets/custom.css";
import { gsap } from "gsap";

export default {
  name: "DataTableComponent",
  data() {
    return {
      sections: sectionData,
      selectedTab: 0,
      activeAccordion: 0,
      isDesktop: false,
    };
  },
  mounted() {
    this.checkScreenSize();
    window.addEventListener("resize", this.checkScreenSize);
  },
  beforeDestroy() {
    window.removeEventListener("resize", this.checkScreenSize);
  },
  methods: {
    selectTab(index) {
      this.selectedTab = index;
      this.animateContent(this.$refs.tabContent);
    },
    toggleAccordion(index) {
      this.activeAccordion = this.activeAccordion === index ? null : index;
      this.$nextTick(() => {
        this.animateContent(this.$refs.accordionContent);
      });
    },
    checkScreenSize() {
      this.isDesktop = window.innerWidth >= 768;
    },
    animateContent(element) {
      gsap.fromTo(
        element,
        { opacity: 0, y: 20 },
        { opacity: 1, y: 0, duration: 0.5, ease: "power2.out" }
      );
    },
  },
};
</script>
