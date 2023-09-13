<template>
  <nav class="sticky bottom-0 z-10 bg-white">
    <ul class="flex items-center justify-around border-t">
      <NavItem
        v-for="(value, key) in NAV_ITEMS"
        :key="key"
        :href="`#${key}`"
        :class="{ 'bg-gray-200 pointer-events-none': key === currentPage }"
        @click="emit('navigate', key)"
      >
        <component :is="value" class="h-6 w-6" /> {{ key }}
      </NavItem>
    </ul>
  </nav>
</template>

<script setup>
import NavItem from "./NavItem.vue";
import { NAV_ITEMS } from "../constants";
import { isPageValid } from "../validators";

defineProps({
  currentPage: {
    required: true,
    type: String,
    validator: isPageValid,
  },
});
const emit = defineEmits({
  navigate: isPageValid,
});
</script>