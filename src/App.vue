<template>
  <div id="nav">
    <ul class="nav">
      <li class="nav-item">
        <a class="nav-link active" href="#">
          <router-link to="/" style="text-decoration: none">Task</router-link>
        </a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">
          <router-link to="/profile">Profile</router-link>
        </a>
      </li>
    </ul>
  </div>
  <router-view />
</template>

<style lang="scss">
html,
body {
  height: 100%;
  font-size: 16px;
  scroll-behavior: smooth;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  // text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 8px 30px;
  background: #d7d6d3;
  a {
    font-weight: bold;
    color: #2c3e50;
    text-decoration: none !important;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
