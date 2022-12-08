<template>
  <div class="container">
 <h3 class="mb-4" style="color:#008080;">Daftar Parameter</h3>
 <ParameterTable />
</div>
  
</template>
<script>

import ParameterTable from '@/components/ParameterTable.vue'
export default {

  components: {
    ParameterTable
},
}
</script>

<style>
.container {
  max-width: 100rem;
  margin: 10rem auto;
  display: flex;
  justify-content: center;
  flex-direction: column;
  padding: 2rem;
  border: 1px solid #ccc;
  border-radius: 12px;
}

</style>