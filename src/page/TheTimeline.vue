<template>
  <div class="mt-7">
    <ul>
      <TimelineItem
        v-for="item in timelineItems"
        :key="item.hour"
        :timeline-item="item"
      />
    </ul>
  </div>
</template>

<script setup>
import TimelineItem from "../components/TimelineItem.vue";
import { validateTimelineItems } from "../validators";

defineProps({
  timelineItems: {
    required: true,
    type: [Object],
    validator: validateTimelineItems,
  },
});
</script>