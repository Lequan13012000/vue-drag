<script setup lang="ts">
import { ref } from "vue";
import draggable from "vuedraggable";

const message = [
    "vue.draggable",
    "draggable",
    "component",
    "for",
    "vue.js 2.0",
    "based",
    "on",
    "Sortablejs"
];
let order = message.length;

const list = ref(
    message.map((name, index) => {
        return { name, order: index + 1 };
    })
);

const sort = () => {
    list.value = list.value.sort((a, b) => a.order - b.order);
};

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
        <div class="col-2">
            <button class="btn btn-secondary button" @click="sort">
                To original order
            </button>
        </div>

        <div class="col-6">
            <h3>Transition</h3>
            <draggable class="list-group" item-key="order" tag="transition-group"
                :component-data="{ tag: 'ul', name: 'flip-list', type: 'transition' }" v-model="list" v-bind="dragOptions"
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
  