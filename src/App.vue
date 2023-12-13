<script setup lang="ts">
import { ref, watch } from 'vue';
import TheWelcome from './components/TheWelcome.vue'

const listCustomer = ref([
  {
    id: 1,
    name: "Họ và tên",
    items: [
      {
        id: 1,
        name: 'Lê Đoàn Anh Quân',
      },
      {
        id: 2,
        name: 'Lê Đoàn Tuấn Vũ',
      }
    ]
  },
  {
    id: 2,
    name: "Ngày sinh",
    items: [
      {
        id: 1,
        name: '10/06/2000',
      },
      {
        id: 2,
        name: '10/11/2003',
      }
    ]
  },
  {
    id: 3,
    name: "Giới tính",
    items: [
      {
        id: 1,
        name: 'Nam',
      },
      {
        id: 2,
        name: 'Nữ',
      }
    ]
  },
]);
watch(listCustomer, (newRoot) => {
  console.log(newRoot);
}, { deep: true });
</script>

<template>
  <main>
    <TheWelcome :nodes="listCustomer" />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
