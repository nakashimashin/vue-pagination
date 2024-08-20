<script setup lang="ts">
import { ref, computed } from 'vue';
import '@mdi/font/css/materialdesignicons.css';


const page = ref(1);


const data = ref([
  { id: 1, title: 'ワンピース' },
  { id: 2, title: 'ドラゴンボール' },
  { id: 3, title: 'ヒーローアカデミア' },
  { id: 4, title: '鬼滅の刃' },
  { id: 5, title: 'ブリーチ' },
  { id: 6, title: '銀魂' },
  { id: 7, title: 'ニセコイ' },
  { id: 8, title: 'ウィッチウォッチ' },
  { id: 9, title: 'ジョジョの奇妙な冒険' },
  { id: 10, title: '呪術廻戦' }
]);


const itemsPerPage = 3;


const paginatedData = computed(() => {
  const start = (page.value - 1) * itemsPerPage;
  const end = start + itemsPerPage;
  return data.value.slice(start, end);
});


const totalPages = computed(() => {
  return Math.ceil(data.value.length / itemsPerPage);
});

</script>

<template>
  <main>
    <table>
      <thead>
        <tr>
          <th>ID</th>
          <th>タイトル</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in paginatedData" :key="item.id">
          <td>{{ item.id }}</td>
          <td>{{ item.title }}</td>
        </tr>
      </tbody>
    </table>


    <v-pagination
      v-model="page"
      :length="totalPages"
      total-visible="1"
      @input="page = $event"
      prev-icon="mdi-chevron-left"
      next-icon="mdi-chevron-right"
      active-color="red"
    ></v-pagination>
  </main>
</template>

<style scoped>
table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
}

th, td {
  border: 1px solid #ddd;
  padding: 8px;
  text-align: left;
}

th {
  background-color: #f2f2f2;
}

.pagination {
  margin-top: 10px;
  text-align: center;
}

button {
  padding: 5px 10px;
  margin: 0 5px;
}

button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
</style>
