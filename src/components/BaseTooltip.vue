<template>
  <div class="relative">
    <div
      class="flex items-center h-full"
      @mouseenter="isShown = true"
      @mouseleave="isShown = false6"
      @click="isShown = false"
    >
      <slot />
    </div>
    <transition>
      <div v-show="isShown" :class="classes">{{ text }}</div>
    </transition>
  </div>
</template>

<style scoped>
.v-enter-active {
  transition: opacity 200ms ease-out;
}

.v-leave-active {
  transition: opacity 75ms ease-in;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>

<script>
export default {
  data() {
    return {
      isShown: false,
      classes: [
        "bg-gray-600",
        "bg-opacity-60",
        "rounded-sm",
        "text-white",
        "text-xs",
        "whitespace-nowrap",
        "p-2",
        "absolute",
        "transform",
        this.positionClasses(),
      ],
    };
  },

  props: {
    text: String,
    top: Boolean,
    left: Boolean,
    right: Boolean,
  },

  methods: {
    positionClasses() {
      const classTop = this.top ? "bottom-12" : "top-14";

      if (this.left) {
        return [classTop, "right-0"];
      }

      if (this.right) {
        return [classTop, "left-0"];
      }

      return [classTop, "left-1/2", "-translate-x-1/2"];
    },
  },
};
</script>
