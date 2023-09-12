<template>
  <TheHeader
    @go-to-timeline="goTo(PAGE_TIMELINE)"
    @go-to-progress="goTo(PAGE_PROGRESS)"
  />
  <main class="flex flex-grow flex-col">
    <TheTimeline v-show="currentPage === PAGE_TIMELINE" />
    <TheActivities v-show="currentPage === PAGE_ACTIVITIES" />
    <TheProgress v-show="currentPage === PAGE_PROGRESS" />
  </main>
  <TheNav :current-page="currentPage" @navigate="goTo($event)" />
</template>

<script setup>
import { ref } from "vue";

import { PAGE_TIMELINE, PAGE_ACTIVITIES, PAGE_PROGRESS } from "./constants";
import { normalizePageHash } from "./functions";

import TheHeader from "./components/header/TheHeader.vue";
import TheNav from "./components/TheNav.vue";
import TheTimeline from "./page/TheTimeline.vue";
import TheActivities from "./page/TheActivities.vue";
import TheProgress from "./page/TheProgress.vue";

const currentPage = ref(normalizePageHash());

function goTo(page) {
  currentPage.value = page;
}
</script>
