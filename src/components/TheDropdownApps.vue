<template>
  <div class="relative">
    <BaseTooltip text="YouTube apps">
      <button @click="isOpen = !isOpen" class="relative p-2 focus:outline-none">
        <BaseIcon name="viewGrid" class="w-5 h-5" />
      </button>
    </BaseTooltip>

    <transition>
      <div
        v-show="isOpen"
        ref="dropdown"
        @keydown.esc="isOpen = false"
        tabindex="-1"
        :class="dropdownClasses"
      >
        <section class="py-2 border-b">
          <ul>
            <DropdownAppsListItem label="YouTube TV" />
          </ul>
        </section>
        <section class="py-2 border-b">
          <ul>
            <DropdownAppsListItem label="YouTube Music" />

            <DropdownAppsListItem label="YouTube Kids" />
          </ul>
        </section>
        <section class="py-2">
          <ul>
            <DropdownAppsListItem label="Creator Academy" />
            <DropdownAppsListItem label="YouTube for Artists" />
          </ul>
        </section>
      </div>
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
import BaseIcon from "./BaseIcon.vue";
import BaseTooltip from "./BaseTooltip.vue";
import DropdownAppsListItem from "./DropdownAppsListItem.vue";

export default {
  components: {
    BaseIcon,
    BaseTooltip,
    DropdownAppsListItem,
  },

  data() {
    return {
      isOpen: false,
    };
  },

  mounted() {
    window.addEventListener("click", (event) => {
      if (!this.$el.contains(event.target)) {
        this.isOpen = false;
      }
    });
  },

  watch: {
    isOpen() {
      this.$nextTick(() => this.isOpen && this.$refs.dropdown.focus());
    },
  },

  computed: {
    dropdownClasses() {
      return [
        "z-10",
        "absolute",
        "top-9",
        "right-0",
        "sm:left-0",
        "bg-white",
        "w-60",
        "border",
        "border-t-0",
        "focus:outline-none",
      ];
    },
  },
};
</script>
