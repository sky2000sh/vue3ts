<!--/* ##################################################
# 화면명 : 화면명을 적어주세요.
# DESC   : 기본검색화면 소스입니다. 카피해 사용해 주세요.
# 작성자 : XXX
# 생성일 : 20XX.XX.XX
######################################################### */-->

<!-- composition-ts.vue 엔터 -->
<!-- setting 설정에서 vetur template를 검색해서 첫번째에 있는
Template Interpolation Service
Enable template interpolation service that offers hover / definition / references in Vue interpolations.
여기 체크박스에 체크를 해줘야 template안에 definition이나 ref들을 인지해서 알려준다. -->

<template>
<div class="job-list">
    <p>Ordered by {{ order }}</p>
    <transition-group name="list" tag="ul">
        <li v-for="job in orderedJobs" :key="job.id">
            <h2>{{ job.title }} in {{ job.location }} </h2>
            <div class="salary">
                <p>{{ job.salary.toLocaleString() }} euro </p>
            </div>
            <div class="description">
                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit.
                    Reiciendis voluptates earum accusantium provident quis, aliquam sit architecto officia.
                    Molestiae vero non quos accusamus debitis obcaecati a quaerat dignissimos dolores eligendi?</p>
            </div>
        </li>
    </transition-group>
</div>

</template>

<script lang="ts">
import { computed, defineComponent, PropType } from 'vue'
import Job from '@/types/index'
import orderTerm from '@/types/orderTerm'

export default defineComponent({
  props: {
    jobs: {
      required: true,
      type: Array as PropType<Job[]>
    },
    order: {
      required: true,
      type: String as PropType<orderTerm>
    }
  },

  setup (props) {
    const orderedJobs = computed(() => {
      return [...props.jobs].sort((a: Job, b: Job) => {
        return a[props.order] > b[props.order] ? 1 : -1
      })
    })

    return { orderedJobs }
  }

})
</script>

<style scoped>
    .job-list {
        max-width: 960px;
        margin:40px auto;
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

    .list-move {
      transition: all 1s;
      /* 1s, 2s => second의 의미 (시간) */
    }
</style>
