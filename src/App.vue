<template >

  <!-- <TableData :item="listItems" /> -->

  <CrudCmp />
</template>


<script>


// import TableData from './components/TableData.vue'
import CrudCmp from './components/CrudCmp.vue'

export default {
  name: 'App',
  components: {
    // TableData,
    CrudCmp

  },
  data() {
    return {
      listItems: [],
    }

  },

  methods: {
    async getData() {
      const res = await fetch("https://jsonplaceholder.typicode.com/users");
      const finalRes = await res.json();
      this.listItems = finalRes;

    },

  },
  created() {
    // this.getData();
  }



}
</script>

<style>

</style>
