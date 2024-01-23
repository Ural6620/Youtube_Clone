<template>
  <div class="relative">
    <BaseTooltip text="Settings">
      <button @click="toggle" class="relative p-2 focus:outline-none">
        <BaseIcon name="dotsVertical" class="w-5 h-5" />
      </button>
    </BaseTooltip>
    <transition>
      <div
        v-show="isOpen"
        ref="dropdown"
        @keydown.esc="close"
        tabindex="-1"
        :class="dropdownClasses"
      >
        <component
          v-if="selectedMenu"
          :is="menu"
          :selected-options="selectedOptions"
          @select-option="selectOption"
          @close="closeMenu"
        />
        <TheDropdownSettingsMain
          v-else
          :menu-items="menuItems"
          @select-menu="selectMenu"
        />
      </div>
    </transition>
  </div>
</template>

<style scoped>
.v-enter-active {
  transition: all 200ms ease-out;
}
.v-leave-active {
  transition: all 75ms ease-in;
}
.v-enter-from,
.v-leave-to {
  opacity: 0;
  scale: 0.95;
}
</style>

<script>
import BaseIcon from "./BaseIcon.vue";
import BaseTooltip from "./BaseTooltip.vue";
import TheDropdownSettingsMain from "./TheDropdownSettingsMain.vue";
import TheDropdownSettingsAppearence from "./TheDropdownSettingsAppearence.vue";
import TheDropdownSettingsLanguage from "./TheDropdownSettingsLanguage.vue";
import TheDropdownSettingsLocation from "./TheDropdownSettingsLocation.vue";
import TheDropdownSettingsRestrickedMode from "./TheDropdownSettingsRestrickedMode.vue";

export default {
  components: {
    BaseIcon,
    BaseTooltip,
    TheDropdownSettingsMain,
    TheDropdownSettingsAppearence,
    TheDropdownSettingsLanguage,
    TheDropdownSettingsLocation,
    TheDropdownSettingsRestrickedMode,
  },

  data() {
    return {
      isOpen: false,
      selectedMenu: null,
      selectedOptions: {
        theme: {
          id: 0,
          text: "Use device theme",
        },
        language: {
          id: 0,
          text: "English",
        },
        location: {
          id: 0,
          text: "BAA",
        },
        restrictedMode: {
          enabled: false,
          text: "Off",
        },
      },
      dropdownClasses: [
        "z-10",
        "absolute",
        "top-9",
        "-right-full",
        "sm:right-0",
        "bg-white",
        "w-72",
        "border",
        "border-t-0",
        "focus:outline-none",
      ],
    };
  },

  mounted() {
    window.addEventListener("click", (event) => {
      if (!this.$el.contains(event.target)) {
        this.close();
        this.closeMenu();
      }
    });
  },

  computed: {
    menu() {
      const menuComponentNames = {
        appearence: "TheDropdownSettingsAppearence",
        language: "TheDropdownSettingsLanguage",
        location: "TheDropdownSettingsLocation",
        restricted_mode: "TheDropdownSettingsRestrickedMode",
      };
      return this.selectedMenu
        ? menuComponentNames[this.selectedMenu.id]
        : null;
    },

    menuItems() {
      return [
        {
          id: "appearence",
          label: "Appearance: " + this.selectedOptions.theme.text,
          icon: "sun",
          withSubMenu: true,
        },
        {
          id: "language",
          label: "Language: " + this.selectedOptions.language.text,
          icon: "translate",
          withSubMenu: true,
        },
        {
          id: "location",
          label: "Location: " + this.selectedOptions.location.text,
          icon: "globeAlt",
          withSubMenu: true,
        },
        {
          id: "settings",
          label: "Settings",
          icon: "cog",
          withSubMenu: false,
        },
        {
          id: "your_data_in_youtube",
          label: "Your data in YouTube",
          icon: "shielCheck",
          withSubMenu: false,
        },
        {
          id: "help",
          label: "Help",
          icon: "questionMarketCircle",
          withSubMenu: false,
        },
        {
          id: "send_feedback",
          label: "Send feedback",
          icon: "chatAlt",
          withSubMenu: false,
        },
        {
          id: "keyboard_shortcuts",
          label: "Keyboard shortcuts",
          icon: "calculator",
          withSubMenu: false,
        },
        {
          id: "restricted_mode",
          label: "Restricted Mode: " + this.selectedOptions.restrictedMode.text,
          icon: null,
          withSubMenu: true,
        },
      ];
    },
  },

  watch: {
    isOpen() {
      this.$nextTick(() => this.isOpen && this.$refs.dropdown.focus());
    },
  },

  methods: {
    toggle() {
      this.isOpen ? this.close() : this.open();
    },

    open() {
      this.isOpen = true;
    },

    close() {
      this.isOpen = false;

      setTimeout(() => this.closeMenu, 100);
    },

    selectMenu(menu) {
      this.selectedMenu = menu;

      this.$refs.dropdown.focus();
    },

    closeMenu() {
      this.selectMenu(null);
    },

    selectOption(option) {
      this.selectedOptions[option.name] = option.value;
      this.close();
      this.closeMenu();
    },
  },
};
</script>
