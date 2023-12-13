<script setup lang="ts">
import { ref } from 'vue';
import draggable from 'vuedraggable'

const props = defineProps(['nodes']);
</script>
<template>
  <draggable :list="nodes" item-key="name">
    <template #item="{ element }">
      <div scope="row">
        <div class="flex gap-x-5" :class="!element.items ? 'pl-[50px]' : ''">
          <div>{{ element.id }}</div>
          <div>{{ element.name }}</div>
        </div>
        <TheWelcome :nodes="element.items" v-if="element.items">
        </TheWelcome>
      </div>
    </template>
  </draggable>
</template>
<style scoped></style>

