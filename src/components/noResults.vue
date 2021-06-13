<template>
    <div class="container">
    <p id="text_1">Uh-oh!</p>
      <p id="text_2">You look lost on your journey!</p>
      <button id="red_button" type="button" class="btn">Go back home</button>
    </div>
  

</template>


<script>



export default {
  name: 'noResults',

}
</script>
<style>
    #text_1{
  height:43px;
  font-family:'Lato';
  font-style:'normal';
  font-weight:'bold';
  font-size:36px;
  line-height:43px;
  
  align-items:center;
  text-align:center;
  color:#353535;
  margin-bottom:0px;
}

#text_2{
  margin-top:10px;
  margin-bottom:0px;
   font-family:'Lato';
  font-style:'normal';
  font-weight: 500;
  font-size:20px;
  height:30px;
  line-height: 150%;
  text-align:center;
  color:#5E5E5E;
}


#red_button{
   margin-top:25px;

   border-radius:60px;
   background-color:#F22539;

    height:44px;
  width:155px;

  color:#FFFFFF;

  font-family:'Lato';
  font-style: normal;
  font-weight: bold;

  font-size:18px;
  line-height:22px;

  text-align:center;
}
</style>