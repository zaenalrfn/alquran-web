
<template>
  <HeaderSearch/>
  <Item/>
</template>

<script>
  import HeaderSearch from '@/components/HeaderSearch.vue';
  import Item from '@/components/itemAlquran.vue'

  export default {
    name: 'HomeView',
    components: {
      HeaderSearch,
      Item
    }
  }

</script>
  <!-- //  https://equran.id/api/surat -->