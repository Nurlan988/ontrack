<template>
  <div class="mt-7">
    <ul>
      <li
        v-for="item in [0, 1, 2, 3, 4, 5]"
        class="relative flex flex-col gap-2 border-t border-gray-200 py-10 px-4"
        :key="item"
      >
        <a
          href="#"
          class="absolute -top-4 left-1/2 -translate-x-1/2 rounded bg-gray-100 px-2 font-mono text-lg text-gray-500"
        >
          {{ item }}:00
        </a>
      </li>
    </ul>
  </div>
</template>