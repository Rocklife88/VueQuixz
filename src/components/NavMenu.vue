<template>
    <div class="nav-container-box">
<div class="header">
 <div class="logo">
    <RouterLink class="nav-link-logo" to="/">
        <h4>QuizApp</h4> 
    </RouterLink>

 </div>
 <div class="nav-container">
<RouterLink class="nav-links" to="/"> Home</RouterLink>
<RouterLink class="nav-links" to="/about"> About</RouterLink>
 </div>
</div>
        
</div>

</template>

<script setup>
import { RouterLink } from 'vue-router';

</script>

<style  scoped>



.nav-container-box{
    max-width:1100px;
    margin:0 auto;

}
.header{
    height:2rem;
    display:flex;
    justify-content: space-between;
    align-content: center;
    padding:0.8rem;
    padding-left:0;
}



.logo{
    display:flex;
    align-items: center;
    font-size:1.2rem;


}


.nav-container{
    display:flex;
    gap:0.9rem;
}
.nav-links{
    color:black;
    font-size:1.1rem;
    font-weight:500;
    text-decoration:none;
}

.nav-link-logo{
    color:black;
    font-size:1.1rem;
    font-weight:500;
    text-decoration:none;
}

.nav-links:hover{
    color:orange;
    
}
</style>