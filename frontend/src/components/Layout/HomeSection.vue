<template>
  <swiper-section
    :title="
      section.libraryName === undefined
        ? $t(section.name)
        : $t(section.name, { libraryName: section.libraryName })
    "
    :items="items"
    :shape="section.shape" />
</template>

<script setup lang="ts">
import { computed } from 'vue';
import { userLibrariesStore } from '@/store';
import type { HomeSection } from '@/store/userLibraries';

const props = defineProps<{ section: HomeSection }>();

const userLibraries = userLibrariesStore();
const items = computed(() => {
  return userLibraries.getHomeSectionContent(props.section);
});
</script>
