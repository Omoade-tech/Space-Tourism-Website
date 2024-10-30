<template>
    <div>
        <section class="hero">
            <div class="container">
                <div class="row align-items-center">
                    <div class="col-md-6">
                        <h2 class="display-6 mb-3">SO, YOU WANT TO TRAVEL TO</h2>
                        <h1 class="display-1 mb-4">SPACE</h1>
                        <p class="lead mb-5">Let's face it; if you want to go to space,
                             you might as well genuinely go to outer space and not hover kind of on the edge of it.
                             Well sit back, and relax because we'll give you a truly out of this world experience!</p>
                    </div>
                    <div class="image col-md-6 text-center">
                        <img src="C:\Users\Adedoyin Sodiq\Desktop\c_VUE\Space_Tourism_Website\src\assets\home\Display Button States - Desktop and Tablet@3x.png" height="300px" class="btn btn-explore">
                    </div>
           
         </div>
    </div>
</section>
    </div>
</template>

<script>

</script>
<style  scoped>
.hero {
    background-image: url('./src/assets/home/background-home-desktop.jpg');
    background-position: cover;
    color: #ffffff;
    height: 100vh;
    width: 100%;
}
.container{
    padding-top: 250px;
}
img{
    margin-left: 150px;
}
@media screen and (min-width:320px) and (max-width:425px) {
    .hero {
    background-image: url('./src/assets/home/background-home-mobile.jpg');
    background-position: cover;
    color: #ffffff;
    height: 130vh;
}
.image {
    display: flex;
    justify-content: center;
    margin-top: -10px;
  }
  .image img {
    margin-left: 0; 
    height: 200px; 
  }
  .container {
    padding-top: 100px;
  }
}


  
  


</style>