<template>
    
     <table class="table cell-border stripe" id="example">
      <thead class="thead-light">
        <tr class="table" style="background-color: #cdd0d5;">
          <th scope="row">No</th>
           <th scope="row">Nama Parameter</th>
           <th scope="row">Value</th>  
           <th scope="row">Aksi</th>
        </tr>
      </thead>
      
      <tbody>
        <tr v-for="(content, index) in contents" :key="content.id">
          <td style="width:1%; text-align: center;">{{ index + 1}}</td>
          <td>{{content.name}}</td>
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
      .get("https://jsonplaceholder.typicode.com/users")
      .then(response=>{
        this.contents = response.data;
        setTimeout(function(){
        $('#example').DataTable(
            {
              dom: '<"top"lf>rt<"bottom"pi><"clear">',
                filter:false,
                pagingType: 'full_numbers',
                pageLength: 5,
                "language":{
                "info":           "Menampilkan _START_ - _END_ dari _TOTAL_ data",
                "lengthMenu":     "Menampilkan _MENU_ data per halaman",
                "search":         "Fillter Nama Parameter",
                "paginate": {
                    "first":      "Pertama",
                    "last":       "Terakhir",
                    "next":       "Selanjutnya",
                    "previous":   "Sebelumnya"
                },
              }
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
.dataTables_wrapper .dataTables_length{
float: right;
}

.dataTables_filter{
margin-top: 50px;
margin-right: 200px;
  
}

.dataTables_wrapper .dataTables_info{
  float:right;
}
.table-primary {
  background-color: #cdd0d5;
}
</style>

  
