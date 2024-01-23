<template>
  <transition name="opasityOverflow">
    <TheSidebarMobilieOverlay @click="$emit('close')" v-show="isOpen" />
  </transition>
  <transition name="opasityOverflow">
    <aside
      v-show="isOpen"
      ref="mobileSidebar"
      @keydown.esc="$emit('close')"
      tabindex="-1"
      class="w-64 max-h-screen overflow-auto bg-white fixed z-40 outline-none"
    >
      <section class="flex items-center p-4 border-b sticky top-0 bg-white">
        <button @click="$emit('close')" class="ml-2 mr-6 focus:outline-none">
          <BaseIcon name="menu" />
        </button>
        <LogoMain />
      </section>
      <SidebarContent />
    </aside>
  </transition>
</template>

<style>
.opasityOverflow-enter-from {
  opacity: 0;
}
.opasityOverflow-enter-active {
  transition: opacity 5s ease-linear;
}
.opasityOverflow-enter-to {
  opacity: 1;
}
.opasityOverflow-leave-from {
  opacity: 1;
}
.opasityOverflow-leave-active {
  transition: opacity 5s ease-linear;
}
.opasityOverflow-leave-to {
  opacity: 0;
}
</style>

<script>
import LogoMain from "./LogoMain.vue";
import SidebarContent from "./SidebarContent.vue";
import BaseIcon from "./BaseIcon.vue";
import TheSidebarMobilieOverlay from "./TheSidebarMobileOverlay.vue";

export default {
  components: {
    LogoMain,
    SidebarContent,
    BaseIcon,
    TheSidebarMobilieOverlay,
  },

  props: {
    isOpen: Boolean,
  },

  emits: {
    close: null,
  },

  watch: {
    isOpen() {
      this.$nextTick(() => this.isOpen && this.$refs.mobileSidebar.focus());
    },
  },
};
</script>
