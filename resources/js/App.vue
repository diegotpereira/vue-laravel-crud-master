<template>
  <div class="container">
      <nav class="navbar navbar-expand-sm bg-dark navbar-dark">
          <ul class="navbar-nav">
              <li class="nav-item">
                  <router-link to="/" class="nav-link">Home</router-link>
              </li>
              <li class="nav-item">
                  <router-link to="/create" class="nav-link">Criar Postagem</router-link>
              </li>
              <li class="nav-item">
                  <router-link to="/posts" class="nav-link">Postagens</router-link>
              </li>
          </ul>
      </nav><br />
      <div>
          <transition name="fade">
              <router-view></router-view>
          </transition>
      </div>
  </div>
</template>

<script>
export default {

}
</script>

<style>
.fade-enter-active, .fade-leave-active {
    transition: opacity .5s
}

.fade-enter, .fade-leave-active {
    opacity: 0;
}
</style>
