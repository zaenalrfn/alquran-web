<template>
 <nav class="navbar bg-white fixed-top">
  <div class="container-fluid">
    <a class="navbar-brand">Alquran</a>
    <form class="d-flex" role="search" v-on:submit.prevent>
      <input v-model="keyword" class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
      <button  class="btn btn-outline-success">cari</button>
    </form>
  </div>
</nav>
</template>



<script type="text/javascript">
  export default {
    name: 'HeaderSearch',
    // computed: {
      // filterSurah(nama) {
      //   nama.forEach((ns) => {
      //     this.namaSurah.title = ns.nama_latin
      //   })
        // if(this.keyword){
        //   console.log(this.namaSurah)
          // return this.namaSurah.filter((item)=>{
          //   console.log(item)
          //   return item.toLowerCase().includes(this.search.toLowerCase()
          // })
        // }else{
        //   return this.namaSurah;
        // }
      // }
    // }
  }
</script>
