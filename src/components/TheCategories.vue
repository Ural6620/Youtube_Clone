<template>
  <section :class="classes">
    <div
      class="bg-white bg-opacity-95 border-t border-b px-4 max-w-screen-2xl m-auto"
    >
      <div class="py-3 flex space-x-3 overflow-auto text-sm whitespace-nowrap">
        <CategoryItem
          v-for="category in categories"
          :key="category"
          :category="category"
          :is-active="category === 'All'"
        />
      </div>
    </div>
  </section>
</template>

<script>
import CategoryItem from "./CategoryItem.vue";
export default {
  components: {
    CategoryItem,
  },

  props: {
    isSidebarOpen: Boolean,
  },

  data() {
    return {
      categories: [
        "All",
        "Trucks",
        "Tools",
        "Mashines",
        "Ingenes",
        "Snow",
        "Ships",
        "Roads",
        "Tanks",
        "Building",
        "Mars",
        "Woodwork",
        "Tractors",
        "Songs",
        "TV Shows",
        "Football",
        "Planes",
        "Live",
        "Streets",
        "Math",
        "Programm",
      ],
    };
  },

  computed: {
    classes() {
      return this.isSidebarOpen ? "xl:pl-64" : "md:pl-24";
    },
  },
};
</script>
