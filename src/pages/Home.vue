<template>
  <div style="text-align: center; margin: 2rem 0">
    <h1 class="title">Star Wars</h1>
    <p>
      Type Script, Services, Composition API, Rest API
      <router-link to="/about" class="link" style="text-decoration: underline"
        >and more</router-link
      >
    </p>
  </div>
  <div v-if="loading">
    <Spinner />
  </div>
  <div v-else>
    <table>
      <thead>
        <tr>
          <td>name</td>
          <td>gender</td>
          <td>mass</td>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(p, index) in people.results" :key="index">
          <td>{{ p.name }}</td>
          <td>{{ p.gender }}</td>
          <td>{{ p.mass }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script lang="ts">
import { defineComponent, onMounted, ref } from 'vue'
import DataService from '../services/DataService'
import ResponseData from '../types/ResponseData'
import Peoples from '../types/Peoples'
import Spinner from '../UI/Spinner.vue'

export default defineComponent({
  components: {
    Spinner
  },
  setup() {
    const loading = ref(true as Boolean)
    const people = ref({} as Peoples)

    onMounted(() => {
      getPeople()
    })

    const getPeople = () =>
      DataService.getAll()
        .then((res: ResponseData) => {
          people.value = res.data
          loading.value = false
        })
        .catch((e: Error) => console.log(e))

    return {
      loading,
      people
    }
  }
})
</script>
