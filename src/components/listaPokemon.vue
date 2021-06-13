<template>
  
   <div class="container">
   
   <div class="card mb-2">
   <div class="card-body d-flex justify-content-between py-2">
    <div class="input-group input-group-lg">
                  <span class="input-group-text border-0 px-1" id="basic-addon2"><i class="fas fa-search fa-lg" style="color: #939597;"></i></span>
                  <input type="text" class="form-control form-control-lg rounded" placeholder="Search"
                    aria-label="Search" aria-describedby="basic-addon2" />
                </div></div></div>
    
    </div>
    
  

</template>


<script>
export default {
  name: 'ListaPokemon',

}
</script>

<style>
.container{
    padding:0px;
    display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: center;
}

.form-control {
  border-color: transparent;
}
.input-group-text{
    background-color:white;
}
.input-group{
    border-color:grey;
}
.input-group>.form-control:focus {
  border-color: transparent;
  box-shadow: inset 0 0 0 1px transparent;
}
.btn-link:hover {
  background-color: rgba(0,0,0,.05);
}
.btn-link:active, .btn-link.active {
  background-color: rgba(0,0,0,.05);
}
.btn-link:focus, .btn-link.focus {
  background-color: rgba(0,0,0,.05);
}
.btn-link:active:focus, .btn-link.active:focus {
  background-color: rgba(0,0,0,.05);
}
</style>