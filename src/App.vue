<template>
  <nav class="navbar navbar-dark bg-primary">
  <div class="container">
    <div>
      <img src="L.jpg" width="50" height="50" class="d-inline-block align-top rounded" alt="">
      <router-link to="/" class="navbar-brand mx-2" href="#"><span class="h2">Lefty.</span></router-link>
    </div>
    <div class="d-flex col-xm-4 justify-content-end align-items-center">
      <router-link to="/" class="navbar-brand mx-2 link-hover text-white" href="#">Home</router-link> |
      <router-link to="/shop" class="navbar-brand mx-2 link-hover" href="#">Shop</router-link>
    </div>
    
  </div>
</nav>

  <router-view/>

<footer class="bg-own1 py-4 px-4 my-4-top">
      <div class="container">
          <div class="copyright text-center">
              <span>Copyright &copy; Hansel 2020</span>
          </div>
      </div>
</footer>
</template>

<style>
.link-hover:hover {
  color: var(--dark) !important;
}
#app {
  font-family: arial;
}

.bg-own {
  background-color: rgba(0,0,0,.03);
}

.bg-own1 {
  background-color: rgba(100, 100, 100, 0.212);
}

a {
  font-family: 'Ubuntu', sans-serif;
}

.my-4-top {
  margin-top: 120px !important;
}
</style>