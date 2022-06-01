<template>
  <div class="app">
    <!-- <p>{{name}} - {{age}}</p>
    <button @click="fnCangeName('clerk')">Change Name</button>
    <button @click="fnChangeAge(13)">Change Age</button> -->

    <!-- <p>{{ jobs[0].location }}</p> -->

    <header>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>

    <JobsList :jobs="jobs" :order="order"/>
  </div>
</template>

<script lang="ts">
// import { Options, Vue } from 'vue-class-component'
// import HelloWorld from '@/components/HelloWorld.vue' // @ is an alias to /src

// @Options({
//   components: {
//     // HelloWorld
//   },
//   data () {
//     return {
//       name: 'Link',
//       age: 25 as number | string
//     }
//   },

//   methods: {
//     fnCangeName (name: string) {
//       this.name = name
//       return name
//     },

//     fnChangeAge (age: string | number) {
//       this.age = age
//       return age
//     }
//   }
// })
// export default class HomeView extends Vue {}

import { defineComponent, reactive, ref, toRefs } from 'vue'
import JobsList from '../views/JobsList.vue'
import Job from '../types/index'
import OrderTerm from '../types/orderTerm'

export default defineComponent({
  // name: 'App',
  // components: {
  // },

  name: 'App',
  components: { JobsList },

  setup () {
    // const state = reactive({
    //   name: 'Link',
    //   age: 25 as string | number
    // })

    // state.name = 999 // cannot change type
    // state.age = '26'

    // return { ...toRefs(state) }

    // ==============================================

    // const name = ref('Link')
    // const age = ref < number | string >(25)

    // return { name, age }

    // ==============================================

    // object Job type
    const jobs = ref<Job[]>([
      { title: 'farm worker', location: 'lon lon ranch', salary: 30000, id: 'GY1001' },
      { title: 'quarryman', location: 'death mountain', salary: 40000, id: 'GY1002' },
      { title: 'flute player', location: 'the lost woods', salary: 35000, id: 'GY1003' },
      { title: 'fisherman', location: 'lake hylia', salary: 21000, id: 'GY1004' },
      { title: 'prison guard', location: 'gerudo valley', salary: 32000, id: 'GY1005' }
    ])

    const order = ref<OrderTerm>('title')
    const handleClick = (term: OrderTerm) => {
      order.value = term
    }

    return { jobs, handleClick, order }
  }

  // methods: {
  //   fnCangeName (name: string) {
  //     this.name = name
  //     return name
  //   },

  //   fnChangeAge (age: string | number) {
  //     this.age = age
  //     return age
  //   }
  // }
})

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
