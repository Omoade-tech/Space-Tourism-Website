<template>
    <div>
        
   <nav class="navbar navbar-expand-lg   w-100">
        <div class="container">
            <a class="navbar-brand" href="#">
                <img src="C:\Users\Adedoyin Sodiq\Desktop\c_VUE\Space_Tourism_Website\src\assets\home\Logo.png" alt="Logo" width="50" height="50">
            </a>
            <div class="line-breaker"></div>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
                <span class="navbar-toggler-icon" style="background-color: aliceblue;"></span>
            </button>
            <div class="collapse navbar-collapse justify-content-end" id="navbarNav">
             
                <ul class="navbar-nav">
                    <li class="nav-item">
                      <RouterLink to="/" class="bar">00 Home</RouterLink>
                     
                    </li>
                    <li class="nav-item">
                    <RouterLink to="/destination" class="bar">01 Destination</RouterLink>
                       
                    </li>
                    <li class="nav-item">
                    <RouterLink to="/crew" class="bar">02 Crews</RouterLink>
                       
                    </li>
                    <li class="nav-item">
                    <RouterLink to="/technology" class="bar">03 Technology</RouterLink>
                      
                    </li>
                </ul>
            </div>
        </div>
    </nav>


<RouterView />

    </div>
</template>



<style scoped>
.bar {
    text-decoration: none;
    margin: 0 20px;
    color: #ffffff;
}
.navbar{
    background-color:#132549;
    position: fixed;
}
@media screen and (min-width: 320px) and (max-width:425px) {
    .navbar-nav{
        width: 50%;
        /* background-color: none; */
        position: absolute;
        right: -20px;
    }
   
    .navbar-toggler{
        margin-right: -20px;
        position: absolute;
        right: 20px;
    }
}
/* @media screen and (min-width: 426px) and (max-width:768px) {
    .navbar-nav{
        width: 50%;
    
        position: absolute;
        right: -240px;
    }
   
    .navbar-toggler{

        position: absolute;
        right: 20px;
    }
} */

</style>