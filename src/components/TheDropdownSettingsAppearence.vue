<template>
  <DropdownSettingsHeader title="Appearence" @back="$emit('close')" />

  <div class="text-gray-500 text-xs p-3">
    Setting applies to this browser only
  </div>

  <section class="py-2">
    <ul class="max-h-96 overflow-auto">
      <DropdownSettingListItem
        v-for="(themeName, themeId) in thems.slice(0, 8)"
        :key="themeId"
        :label="themeName"
        :active="themeId === selectedOptions.theme.id"
        @click="selectOption({ id: themeId, text: themeName })"
      />
    </ul>
  </section>
</template>

<script>
import DropdownSettingsHeader from "./DropdownSettingsHeader.vue";
import DropdownSettingListItem from "./DropdownSettingsListItem.vue";

export default {
  components: {
    DropdownSettingsHeader,
    DropdownSettingListItem,
  },

  props: ["selectedOptions"],

  emits: ["close", "select-option"],

  data() {
    return {
      thems: ["Use device theme", "Dark theme", "Light theme"],
    };
  },

  methods: {
    selectOption(theme) {
      this.$emit("select-option", { name: "theme", value: theme });
    },
  },
};
</script>
