<template>
  <section class="py-2 border-b">
    <ul>
      <DropdownSettingListItem
        v-for="menuItems in menuItems.slice(0, 8)"
        :key="menuItems.label"
        :label="menuItems.label"
        :icon="menuItems.icon"
        :with-sub-menu="menuItems.withSubMenu"
        @click.stop="selectMenu(menuItems)"
      />
    </ul>
  </section>
  <section class="py-2">
    <ul>
      <DropdownSettingListItem
        :label="menuItems[8].label"
        :icon="menuItems[8].icon"
        :with-sub-menu="menuItems[8].withSubMenu"
        @click.stop="selectMenu(menuItems[8])"
      />
    </ul>
  </section>
</template>

<script>
import DropdownSettingListItem from "./DropdownSettingsListItem.vue";

export default {
  components: {
    DropdownSettingListItem,
  },

  props: ["menuItems"],

  emits: ["select-menu"],

  methods: {
    selectMenu(menuItem) {
      if (menuItem.withSubMenu) {
        this.$emit("select-menu", menuItem);
      }
    },
  },
};
</script>
