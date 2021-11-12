<template>
  
<div>
  <nav class="navbar navbar-expand-sm bg-dark ">
    <div class="container-fluid">
      <ul class="navbar-nav">
        <li class="nav-item">
          <router-link class="nav-link" to="/">Home</router-link> |
        </li>
        <li class="nav-item">
          <router-link class="nav-link" to="/about">About</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" to="/login">Login</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" to="/signup">SignUp</router-link>
        </li>
      </ul>
    </div>
  </nav>
      
      <router-view/>
  </div>
</template>

