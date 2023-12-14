<script setup lang="ts">
import { ref } from 'vue';
import draggable from 'vuedraggable'

const props = defineProps(['nodes', 'isChild']);
const isEnd = ref(false);

const dragOptions = ref({
  animation: 0,
  group: "description",
  disabled: false,
  ghostClass: "ghost"
});
const myArray = ref([{ id: 1, name: "Abby", sport: "basket" },
{ id: 2, name: "Brooke", sport: "foot" },
{ id: 3, name: "Courtenay", sport: "volley" },
{ id: 4, name: "David", sport: "rugby" }])
const onEnd = () => {
  console.log('end');
  isEnd.value = true;
  setTimeout(() => {
  isEnd.value = false;
  }, 5000);
}
</script>
<template>
  <div class="flex gap-x-[5rem]">
    <div>
      <!-- <div class="flex gap-x-5" v-if="!isChild">
        <div>Số thứ tự</div>
        <div>Thứ tự ưu tiên</div> 
        <div>Tên trường dữ liệu</div>
        <div>Nguồn dữ liệu</div>
      </div> -->
      <draggable :list="nodes" item-key="name" @end="onEnd">
        <template #item="{ element }">
          <div :class="[!isChild ? 'item' : '', isEnd ? 'flip-list-move' : 'no-move']">
            <div class=" flex gap-x-5" :class="!element.items ? 'pl-[50px]' : ''">
              <div>{{ element.id }}</div>
              <div>{{ element.name }}</div>
            </div>
            <VDraggable :nodes="element.items" v-bind="dragOptions" v-if="element.items" :isChild="true">
            </VDraggable>
          </div>
        </template>
      </draggable>
    </div>
    <div v-if="!isChild">
      <div class="text-[#00c829]">Value Change</div>
      <div>
        <pre class="text-start text-xs">
          {{ nodes }}
        </pre>
      </div>
    </div>
  </div>
</template>
<style scoped>
.item {
  border: 1px solid #ccc;
  margin-top: 16px;
  padding: 16px;
  cursor: move;
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
</style>

