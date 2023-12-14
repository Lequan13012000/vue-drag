<script setup lang="ts">
import { ref } from "vue";
import draggable from "vuedraggable";

const message = [
  {
    "name": "vue.draggable",
    "order": 1
  },
  {
    "name": "draggable",
    "order": 2
  },
  {
    "name": "component",
    "order": 3
  },
  {
    "name": "for",
    "order": 4
  },
  {
    "name": "vue.js 2.0",
    "order": 5
  },
  {
    "name": "based",
    "order": 6
  },
  {
    "name": "on",
    "order": 7
  },
  {
    "name": "Sortablejs",
    "order": 8
  }
]

const dragOptions = {
  animation: 0,
  group: "description",
  disabled: false,
  ghostClass: "ghost"
};

let isDragging = ref(false);
</script>
<template>
  <div class="row">
    <div class="col-6">
      <h3>Transition</h3>
      <draggable class="list-group" item-key="order" tag="transition-group"
        :component-data="{ tag: 'ul', name: 'flip-list', type: 'transition' }" :list="message" v-bind="dragOptions"
        @start="isDragging = true" @end="isDragging = false">
        <template #item="{ element }">
          <li class="list-group-item">
            <i :class="element.fixed ? 'fa fa-anchor' : 'glyphicon glyphicon-pushpin'
              " @click="element.fixed = !element.fixed" aria-hidden="true"></i>
            {{ element.name }}
          </li>
        </template>
      </draggable>
    </div>

    <rawDisplayer class="col-3" :value="list" title="List" />
  </div>
</template>
  
  
<style>
.button {
  margin-top: 35px;
}

.flip-list-move {
  transition: transform 0.5s;
}

.no-move {
  transition: transform 0s;
}

.ghost {
  opacity: 0.5;
  background: #c8ebfb;
}

.list-group {
  min-height: 20px;
}

.list-group-item {
  cursor: move;
}

.list-group-item i {
  cursor: pointer;
}
</style>
  