<template>
  <TheHeader @navigate="goTo($event)" />
  <main class="flex flex-grow flex-col">
    <TheTimeline
      v-show="currentPage === PAGE_TIMELINE"
      :timeline-items="timelineItems"
      :activity-select-options="activitySelectOptions"
    />
    <TheActivities
      v-show="currentPage === PAGE_ACTIVITIES"
      :activities="activities"
    />
    <TheProgress v-show="currentPage === PAGE_PROGRESS" />
  </main>
  <TheNav :current-page="currentPage" @navigate="goTo($event)" />
</template>

<script setup>
import { ref } from "vue";

import { PAGE_TIMELINE, PAGE_ACTIVITIES, PAGE_PROGRESS } from "./constants";
import {
  normalizePageHash,
  generateTimelineItems,
  generateActivitySelectOptions,
} from "./functions";

import TheHeader from "./components/header/TheHeader.vue";
import TheNav from "./components/TheNav.vue";
import TheTimeline from "./page/TheTimeline.vue";
import TheActivities from "./page/TheActivities.vue";
import TheProgress from "./page/TheProgress.vue";

const currentPage = ref(normalizePageHash());

function goTo(page) {
  currentPage.value = page;
}

const timelineItems = generateTimelineItems();

const activities = ["Coding", "Reading", "Traning"];

const activitySelectOptions = generateActivitySelectOptions(activities);
</script>
