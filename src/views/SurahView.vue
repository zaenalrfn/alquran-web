<style scoped>
  .surah {
    padding-top: 5rem;
  }
</style>

<template>

  <HeaderSurah/>

  <div class="surah">
    <div class="container">
      <div class="row pt-3">

        <nav style="--bs-breadcrumb-divider: url(&#34;data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='8' height='8'%3E%3Cpath d='M2.5 0L1 1.5 3.5 4 1 6.5 2.5 8l4-4-4-4z' fill='%236c757d'/%3E%3C/svg%3E&#34;);" aria-label="breadcrumb">
          <ol class="breadcrumb">
            <li class="breadcrumb-item">
              <router-link to="/">
              <a href="#" style="color: #1c3a6e;">Home</a>
              </router-link>
            </li>
            <li class="breadcrumb-item active" aria-current="page">{{ surahAlquran.nama_latin }}</li>
          </ol>
        </nav>
        <!-- <h1>سمِ اللّٰهِ الرَّحْمٰنِ الرَّحِيْمِ </h1> -->
        <div class="col-md-12" v-for="ayat in surahAlquran.ayat" v-bind:key="ayat.id">
          <div class="card border-0 border-bottom p-4 rounded-0">
            <div class="card-body">
              <p class="nomor">{{ ayat.surah }} : {{ ayat.nomor }}</p>
              <h3 class="ayat fs-1">{{ ayat.ar }}</h3>
              <p class="arti-ayat mt-4">{{ ayat.idn }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>


  </div>
</template>

<script type="text/javascript">
  import axios from 'axios'
  import HeaderSurah from '@/components/HeaderSurah.vue'
  export default {
    name: 'SurahView',
    components: {
      HeaderSurah
    },
    data() {
      return {
        surahAlquran: [],
      }
    },
    mounted() {
      let parameter = this.$route.params.id
      axios.get(`https://equran.id/api/surat/${parameter}`)
           .then((surah) => {
              this.surahAlquran = surah.data
           })
    }
  }
</script>
