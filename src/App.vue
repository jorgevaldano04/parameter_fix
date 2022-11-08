<template>
  <div class="container">
 <h2 class="mb-4" style="color:#008080;">Daftar Parameter</h2>
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
  max-width: 70rem;
  margin: 2rem auto;
  display: flex;
  justify-content: center;
  flex-direction: column;
  padding: 2rem;
  border: 2px solid #ccc;
  border-radius: 12px;
}

</style>