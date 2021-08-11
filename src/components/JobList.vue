<template>
  <div class="job-list">
    <p>Order by {{ order }}</p>
    <ul>
      <li v-for="job in orderJobs" :key="job.id">
        <h1>{{ job.title }} in {{ job.location }}</h1>
        <div class="salary">
          <p>{{ job.salary }} naira</p>
        </div>
        <div class="discription">
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolore
            ipsam nam molestiae quam quia, aliquam, itaque consectetur totam
            asperiores eaque impedit error ratione eveniet iure? Est asperiores
            atque tempore perferendis.
          </p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import IJob from '@/types/Jobs'
import OrderTerm from '@/types/OrderTerm'
import { computed, defineComponent, PropType } from 'vue'

export default defineComponent({
  name: "JobList",
  props: {
    jobs: {
      type: Array as PropType<IJob[]>,
      required: true
    },
    order: {
      type: String as PropType<OrderTerm>,
      required: true
    }
  },
  setup(props) {
    const orderJobs = computed(() => {
      return [...props.jobs].sort((a: IJob, b: IJob) => {
        return a[props.order] > b[props.order] ? 1 : -1
      })
    })
    return { orderJobs }
  }
})
</script>

<style>
.job-list {
  max-width: 960px;
  margin: 40px auto;
}
.job-list ul {
  padding: 0;
}
.job-list li {
  list-style-type: none;
  background: white;
  padding: 16px;
  margin: 16px 0;
  border-radius: 4px;
}
.job-list h2 {
  margin: 0 0 10px;
  text-transform: capitalize;
}
.salary {
  display: flex;
}
.salary img {
  width: 30px;
}
.salary p {
  color: #17bf66;
  font-weight: bold;
  margin: 10px 4px;
}
</style>
