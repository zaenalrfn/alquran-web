<template>
 <nav class="navbar bg-white fixed-top">
  <div class="container-fluid">
    <a class="navbar-brand">Alquran</a>
    <form class="d-flex" role="search">
      <input v-model="keyword" class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
      <button @click="searchSurah(keyword)" class="btn btn-outline-success">Search</button>
    </form>
  </div>
</nav>
</template>



<script type="text/javascript">
  // import {namaSurah} from '@/components/itemAlquran.vue'
  export default {
    name: 'HeaderSearch',
    data() {
      return {
        keyword: ""
      }
    },
    methods: {
      searchSurah(key) {
        return console.log(key)
      }
    },
    mounted() {
      // console.log(namaSurah)
    }

  }
</script>
