<template>
  <div class="container">
 <h2 class="mb-4" style="color:#008080;">Daftar Parameter</h2>
   <table class="table table-striped" id="example">
    <thead class="thead-light">
      <tr class="table-primary">
        <th scope="col">No</th>
         <th scope="col">Nama Parameter</th>
         <th scope="col">Value</th>  
         <th scope="col">Aksi</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(user, index) in users" :key="user.id">
        <td>{{ index + 1 }}</td>
        <td>{{user.name}}</td>
        <td>{{user.username}}</td>
        <td><ButtonDetail :visible="false" variant="success">email: {{ user.email }}</ButtonDetail></td>
    
      </tr>
      
    </tbody>
  </table>
</div>
  
</template>
<script>
//Bootstrap and jQuery libraries
import 'bootstrap/dist/css/bootstrap.min.css'; //for table good looks
import 'jquery/dist/jquery.min.js';
//Datatable Modules
import "datatables.net-dt/js/dataTables.dataTables"
import "datatables.net-dt/css/jquery.dataTables.min.css"
import "datatables.net-buttons/js/dataTables.buttons.js"
import "datatables.net-buttons/js/buttons.colVis.js"
import $ from 'jquery'; 
import axios from 'axios'; //for api calling
import ButtonDetail from '@/components/ButtonDetail.vue'
export default {
  name:"App",
  data(){
    return{
      users:[]
    };
  },
 
  mounted(){
    //Web api calling for dynamic data and you can also use into your demo project
    axios
    .get("https://jsonplaceholder.typicode.com/users")
    .then((res)=>
    {
      this.users = res.data;
      setTimeout(function(){
      $('#example').DataTable(
          {
              pagingType: 'full_numbers',
                pageLength: 5,
                processing: true,
          }
      );
      },
        );
    })
  },
  components: {
    ButtonDetail
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