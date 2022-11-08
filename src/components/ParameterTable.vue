<template>
    
     <table class="table table-bordered" id="example">
      <thead class="thead-light">
        <tr class="table-primary">
          <th scope="row">No</th>
           <th scope="row">Nama Parameter</th>
           <th scope="row">Value</th>  
           <th scope="row">Aksi</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(content, index) in contents" :key="content.id">
          <td>{{ index + 1}}</td>
          <td>{{content.description}}</td>
          <td>{{content.valueParameter}}</td>
          <td><ButtonDetail :visible="false" variant="success">Module Name <br>{{ content.moduleName }}<br>
          Parameter Name <br>{{content.parameterName}}
          <br>Deskripsi <br>{{content.description}}</ButtonDetail></td>
      
        </tr>
        
      </tbody>
    </table>
  
    
  </template>
  <script>
  //Bootstrap and jQuery libraries
  import 'bootstrap/dist/css/bootstrap.min.css';
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
    name:'ParameterTable',
    data(){
      return{
        contents:[]
      };
    },
   
    mounted(){
      //Web api calling for dynamic data and you can also use into your demo project
      axios
      .get("http://192.168.150.204:8882/pfm/parameter/search/query?search=moduleName%3D%3D%27BNI_PERFORMANCE_MANAGEMENT%27&offset=0&limit=10")
      .then(response=>{
        this.contents = response.data.content;
        setTimeout(function(){
        $('#example').DataTable(
            {
                pagingType: 'full_numbers',
                pageLength: 5,
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
  
