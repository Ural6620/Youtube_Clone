<template>
  <a
    class="flex items-center pl-5 pr-8 py-1.5 text-sm text-black hover:bg-gray-200"
  >
    <BaseIcon :name="icon" class="w-5 h-5 mr-4 text-gray-400" />
    <span>{{ label }}</span>
  </a>
</template>

<script>
import BaseIcon from "./BaseIcon.vue";

export default {
  components: {
    BaseIcon,
  },

  props: {
    icon: String,
    label: String,
  },
};
</script>
