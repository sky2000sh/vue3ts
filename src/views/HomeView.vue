<template>
  <div>{{name}} - {{age}}</div>
  <button @click="fnCangeName('clerk')">Change Name</button>
  <button @click="fnChangeAge(13)">Change Age</button>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component'
// import HelloWorld from '@/components/HelloWorld.vue' // @ is an alias to /src

@Options({
  components: {
    // HelloWorld
  },
  data () {
    return {
      name: 'Link',
      age: 25 as number | string
    }
  },

  methods: {
    fnCangeName (name: string) {
      this.name = name
      return name
    },

    fnChangeAge (age: string | number) {
      this.age = age
      return age
    }
  }
})
export default class HomeView extends Vue {}
</script>
