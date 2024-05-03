<template>
  <div class="app">
  <header>
    <div class="order">
      <button @click="handleClick('title')">Order by title</button>
      <button @click="handleClick('salary')">Order by salary</button>
      <button @click="handleClick('location')">Order by location</button>
    </div>
  </header>

   <JobList :jobs="jobs" :order="order"/>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import JobList from './components/JobList.vue';
import Job from './types/Job';
import OrderTerm from './types/OrderTerm';

export default defineComponent({
  name: 'App',
  components: { JobList },

  setup() {

    const jobs = ref<Job[]>([
      { title: 'Farm worker', location: 'lon lon ranch', salary: 30000, id: '1' },
      { title: 'Quarryman', location: 'death mountain', salary: 50000, id: '2' },
      { title: 'flute player ', location: 'lon lost wood', salary: 20000, id: '3' },
      { title: 'fisherman', location: 'lake hylia', salary: 10000, id: '4' },
      { title: 'prison guard', location: 'gerudo valley', salary: 660000, id: '5' },
    ])

    const order = ref<OrderTerm>('title')

    const handleClick = (term: OrderTerm) => {
      order.value = term
    }

    return { jobs, handleClick, order }

  }
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
