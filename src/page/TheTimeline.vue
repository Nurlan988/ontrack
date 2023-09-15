<template>
  <div class="mt-7">
    <ul>
      <TimelineItem
        v-for="item in timelineItems"
        :key="item.hour"
        :timeline-item="item"
        :activity-select-options="activitySelectOptions"
      />
    </ul>
  </div>
</template>

<script setup>
import TimelineItem from "../components/TimelineItem.vue";
import { validateTimelineItems, validateSelectOptions } from "../validators";

defineProps({
  timelineItems: {
    required: true,
    type: Array,
    validator: validateTimelineItems,
  },
  activitySelectOptions: {
    type: Array,
    required: true,
    validator: validateSelectOptions,
  },
});
</script>