<template>
  <NuxtLink
    :to="localePath(`${to}`)"
    :class="[
      'relative flex items-center justify-center w-full p-2 text-sm text-left transition duration-200 rounded-md basis-full font-md group focus-brand',
      {
        'bg-light-menu-selection dark:bg-dark-menu-selection text-light-distinct dark:text-dark-distinct fill-light-distinct dark:fill-dark-distinct':
          selected == true,
        'text-light-text dark:text-dark-text fill-light-text dark:fill-dark-text hover:bg-light-highlight dark:hover:bg-dark-highlight':
          selected == false && active == true,
        'text-black/20 dark:text-white/40 fill-black/20 dark:fill-white/40':
          selected == false && active == false,
      },
      linkClasses,
    ]"
    :event="active ? '' : 'click'"
  >
    <slot></slot>
  </NuxtLink>
</template>

<script setup lang="ts">
const localePath = useLocalePath();
defineProps<{
  to: string;
  selected: boolean;
  active: boolean;
  linkClasses?: string | undefined;
}>();
</script>
