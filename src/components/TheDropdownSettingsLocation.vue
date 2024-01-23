<template>
  <DropdownSettingsHeader title="Choose your location" @back="$emit('close')" />

  <section class="py-2">
    <ul class="max-h-96 overflow-auto">
      <DropdownSettingListItem
        v-for="(locationName, locationId) in locations.slice(0, 8)"
        :key="locationId"
        :label="locationName"
        :active="locationId === selectedOptions.location.id"
        @click="selectOption({ id: locationId, text: locationName })"
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
      locations: ["BAA", "Uzbekistan", "Russia", "Singapur"],
    };
  },

  methods: {
    selectOption(location) {
      this.$emit("select-option", { name: "location", value: location });
    },
  },
};
</script>
