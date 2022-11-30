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
          <td>{{content.id}}</td>
          <td><ButtonDetail :visible="false" variant="success">Module Name <br>{{ content.moduleName }}<br>
          Parameter Name <br>{{content.parameterName}}
          <br>Deskripsi <br>{{content.description}}<br><label for="fname">Start Date</label><br>
  <input id="fname" placeholder={{content.username}} name="fname"></ButtonDetail></td>
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
                processing: true,
                dom: '<"top"lf>rt<"bottom"pi><"clear">',
                "sInfoFiltered": "",
                pagingType: 'full_numbers',
                pageLength: 5,
                "autoWidth": true,
                "lengthMenu": [[5, 10, 15], [5, 10, 15]],
                "language":{
            "sInfoFiltered": "",
            "sLengthMenu": "Menampilkan _MENU_ data per halaman",
            "sInfo": "Menampilkan _START_ - _END_ dari _TOTAL_ data",
            "search":         "Fillter Nama Parameter",
            "sSearch": '<span class="input-group-addon"><i class="glyphicon glyphicon-search"></i></span>',
            "oPaginate": {
                "sFirst": "Pertama",
                "sPrevious": "Sebelumnya",
                "sNext": "Selanjutnya",
                "sLast": "Terakhir"
            }
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
.table.dataTable{
  width: 100%;
 
}
.dataTables_wrapper .dataTables_length{
float: right;
}

/* .dataTables_filter{
margin-top: 50px;
margin-left: 500px;
  
} */

.dataTables_wrapper .dataTables_info{
  float:right;
}
.table-primary {
  background-color: #BDC7D2;
}
</style>

  
