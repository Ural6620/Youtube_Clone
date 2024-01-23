<template>
  <DropdownSettingsHeader title="Choose your language" @back="$emit('close')" />

  <section class="py-2">
    <ul class="max-h-96 overflow-auto">
      <DropdownSettingListItem
        v-for="(languageName, languageId) in languages.slice(0, 8)"
        :key="languageId"
        :label="languageName"
        :active="languageId === selectedOptions.language.id"
        @click="selectOption({ id: languageId, text: languageName })"
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
      languages: ["English", "Russian", "Uzbek"],
    };
  },

  methods: {
    selectOption(language) {
      this.$emit("select-option", { name: "language", value: language });
    },
  },
};
</script>
