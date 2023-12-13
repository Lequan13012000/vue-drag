<script setup lang="ts">
import { ref } from 'vue';
import draggable from 'vuedraggable'

const listCustomer = ref([
  {
    id: 1,
    name: "Họ và tên",
    items: [
      {
        position: 1,
        user_name: 'Lê Đoàn Anh Quân',
        source: 'CDP - Bảng khách hàng'
      },
      {
        position: 2,
        user_name: 'Lê Đoàn Tuấn Vũ',
        source: 'Saleforce CRM - Bảng khách hàng'
      }
    ]
  },
  {
    id: 2,
    name: "Ngày sinh",
    items: [
      {
        position: 1,
        user_name: '10/06/2000',
        source: 'CDP - NS'
      },
      {
        position: 2,
        user_name: '10/11/2003',
        source: 'Saleforce CRM - NS'
      }
    ]
  },
  {
    id: 3,
    name: "Giới tính",
    items: [
      {
        position: 1,
        user_name: 'Nam',
        source: 'CDP - GT'
      },
      {
        position: 2,
        user_name: 'Nữ',
        source: 'Saleforce CRM - GT'
      }
    ]
  },
]);
</script>
<template>
  <div class="row">
    <div class="col-8">
      <h1 class="mb-3">Draggable table</h1>

      <table class="table table-striped" id="customers">
        <thead class="thead-dark">
          <tr>
            <th scope="col">Số thứ tự</th>
            <th scope="col">Thứ tự ưu tiên</th>
            <th scope="col">Tên trường dữ liệu</th>
            <th scope="col">Nguồn dữ liệu</th>
          </tr>
        </thead>
        <draggable v-model="listCustomer" tag="tbody" item-key="name">
          <template #item="{ element }">
            <div scope="row">
              <div class="flex gap-x-5">
                <div>{{ element.id }}</div>
                <div>{{ element.name }}</div>
              </div>
                <draggable draggable v-model="listCustomer" tag="tbody" item-key="name">
                  <template #item="{ item }">
                    <div class="flex gap-x-[100px] pl-[20px]">
                      <div>{{ item }}</div>
                      <!-- <div>{{ item.user_name }}</div>
                      <div>{{ item.source }}</div> -->
                    </div>
                  </template>
                </draggable>
            </div>
          </template>
        </draggable>
      </table>
    </div>

    <rawDisplayer class="col-3" :value="listCustomer" title="List" />
  </div>
</template>
<style scoped>
#customers {
  font-family: Arial, Helvetica, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

#customers td,
#customers th {
  border: 1px solid #ddd;
  padding: 8px;
}

#customers tr:nth-child(even) {
  background-color: #f2f2f2;
}

#customers tr:hover {
  background-color: #ddd;
}

#customers th {
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: left;
  background-color: #04AA6D;
  color: white;
}
</style>

