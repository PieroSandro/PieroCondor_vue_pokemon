<template>
  
   <div class="container">
   
   <div id="big_input" class="card">
   
    <div class="input-group">
                 <i class="fas fa-search iconsearch"></i>
                  <input type="text" id="input_search" class="form-control rounded" 
                  placeholder="Search"
                   />
                </div></div>
    
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

.card-body{
    max-width:100%;
max-height:100%;
}

.input-group{
    height:50px;
}

.iconsearch{
     font-size:18px;
     color:#BFBFBF;
     height:18px;

     margin-left:15px;
     margin-top:auto;
     margin-bottom:auto;
}

#input_search{
    padding-right:10px;
    padding-left:10px;

    font-family:'Montserrat';
  font-style: normal;
  font-weight: 500;

  font-size:16px;
  line-height:140%;
  
  color:#353535;
  border:none;
  text-decoration: none;
  background-color:#FFFFFF;
  
}

#input_search:focus{
   outline:none;
  box-shadow: none;
}
::-webkit-input-placeholder {
  color: #BFBFBF !important;
}

@media screen and (max-width: 575px) {
  
#big_input{
  margin-top:35px;
  height:50px;
  width:315px;
 
  overflow:hidden;
  border-radius:5px;
  background-color:#FFFFFF;
  box-shadow:0px 2px 10px rgba(0,0,0,0.04);
   border:none;
   
}
        
}

@media screen and (min-width: 576px) {
#big_input{
  margin-top:35px;
  height:50px;
  width:570px;
  overflow:hidden;
  border-radius:5px;
  background-color:#FFFFFF;
  box-shadow:0px 2px 10px rgba(0,0,0,0.04);
   border:none;
  
}
        
}
</style>