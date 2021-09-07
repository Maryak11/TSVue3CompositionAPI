<template>
  <div class="wrapper">
    <Header />
    <div class="wrapper-content">
      <div class="container">
        <router-view />
      </div>
    </div>
    <Footer />
  </div>
</template>

<script lang="ts">
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
interface Person {
  id: number
  title: string
  male: boolean
}

export default {
  components: {
    Header,
    Footer
  },
  data() {
    return {
      wizzar: {
        id: 2432,
        title: 'string',
        male: true
      } as Person
    }
  }
}
</script>

<style lang="scss"></style>
