<template>

<div class="hello">





<form>
  
    
    Email :<input type="email" size="25"  id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email"> <br>
   
  
   Password :<input type="password" size="10" maxlength="8" id="exampleInputPassword1" placeholder="Password">
 
  <br>
  <button type="submit" class="btn btn-primary">Submit</button>
</form>

</div>
    
</template>



<script>
export default {
  name: "Register",
  props: {
    msg: String
  }
};
</script>