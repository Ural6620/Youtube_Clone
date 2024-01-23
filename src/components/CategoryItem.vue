<template>
  <a href="#" :class="classes">{{ category }}</a>
</template>

<script>
export default {
  props: ["category", "isActive"],

  computed: {
    classes() {
      const classes = ["px-3", "py-1", "transition", "border", "rounded-full"];

      return this.isActive
        ? [
            ...classes,
            "bg-gray-600",
            "border-gray-700",
            "hover:bg-gray-500",
            "text-white",
          ]
        : [...classes, "bg-gray-300", "border-gray-100", "hover:bg-gray-200"];
    },
  },
};
</script>
//
