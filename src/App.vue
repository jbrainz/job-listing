<template>
  <div class="app">
    <header>
      <div class="title">
        <h1>Hyrule Jobs</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import IJob from './types/Jobs'
import JobList from './components/JobList.vue'
import OrderTerm from './types/OrderTerm'

export default defineComponent({
  name: "App",
  components: { JobList },
  setup() {
    const jobs = ref<IJob[]>([
      {
        title: 'Front end Developer',
        location: 'Nigeria',
        salary: 40000,
        id: '1'
      },
      {
        title: 'UI Developer',
        location: 'Lagos',
        salary: 12000,
        id: '2'
      },
      {
        title: 'Back end Developer',
        location: 'Ondo',
        salary: 45000,
        id: '3'
      },
      {
        title: 'React Developer',
        location: 'Calabar',
        salary: 20000,
        id: '4'
      },
      {
        title: 'Mobile Developer',
        location: 'Oyo',
        salary: 30000,
        id: '5'
      }
    ])
    const order = ref<OrderTerm>('title')
    const handleClick = (term: OrderTerm) => {
      order.value = term
    }
    return { jobs, handleClick, order }
  },


});
</script>

<style>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>
