<template>
    <div v-if="OpenClose" class="modal fade show" 
    tabindex="-1" aria-labelledby="exampleModalLabel" aria-modal="true" role="dialog"
    style="display:block"
    >
  <div class="modal-dialog">
    
    <div class="modal-content">
      <div class="modal-header">
        <button type="button" class="btn-close" @click="OpenCloseButton()" aria-label="Close"></button>
      </div>
      <div class="modal-body">
     <slot></slot>
      </div>
      <div class="modal-footer">
        <button type="button" @click="OpenCloseButton()" :class="'btn btn-'+variant" >Close</button>
        
      </div>
    </div>
  </div>
</div>
<button type="button" style="background-color:#ff6900" @click="OpenCloseButton()" :class="'btn btn-'+variant" >Detail</button>
</template>

<script>
export default{
    name:'ButtonDetail',
    props:{
        visible: Boolean,
        variant: String,
    },
    data(){
        return{
            OpenClose:this.visible
        }
    },
    methods:{
        OpenCloseButton(){
            this.OpenClose = !this.OpenClose;
        }
    },
    watch:{
        visible: function(newVal, oldVal){
            this.OpenClose = newVal
            console.log('new' + newVal + '==' + oldVal)
        }
    }
}
</script>

<style>
/* The Modal (background) */
.modal {
  display: none; /* Hidden by default */
  position: fixed; /* Stay in place */
  z-index: 1; /* Sit on top */
  padding-top: 100px; /* Location of the box */
  left: 0;
  top: 0;
  width: 100%; /* Full width */
  height: 100%; /* Full height */
  overflow: auto; /* Enable scroll if needed */
  background-color: rgb(0,0,0); /* Fallback color */
  background-color: rgba(0,0,0,0.4); /* Black w/ opacity */
}

/* Modal Content */
.modal-content {
  position: relative;
  background-color: #fefefe;
  margin: auto;
  padding: 0;
  border: 1px solid #888;
  width: 100%;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2),0 6px 20px 0 rgba(0,0,0,0.19);
  -webkit-animation-name: animatetop;
  -webkit-animation-duration: 0.4s;
  animation-name: animatetop;
  animation-duration: 0.4s
}

/* Add Animation */
@-webkit-keyframes animatetop {
  from {top:-300px; opacity:0} 
  to {top:0; opacity:1}
}

@keyframes animatetop {
  from {top:-300px; opacity:0}
  to {top:0; opacity:1}
}

</style>