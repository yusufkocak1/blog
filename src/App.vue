<template>
  <div id="nav">
    <div>
      <router-link class="nav-item" to="/">Home</router-link>
      <router-link class="nav-item" to="/about">About</router-link>
    </div>
    <div>
      <router-link class="nav-item" to="/login">Login</router-link>
    </div>
  </div>
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #fff;
  background-color: #212121;
}

body {
  background-color: #212121;

}

#nav {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 20px;
  border-bottom: 8px solid #FFD93D;
}

.nav-item {
  width: 100px;
  box-shadow: 2px 2px 2px 2px rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  border-radius: 2px;
  padding: 8px;
  padding-left: 16px;
  padding-right: 16px;
  background-color: #6BCB77;
  color: #fff;
  text-decoration: none;
  margin-left: 10px;}

#nav a {
  font-weight: bold;
}

#nav a.router-link-exact-active {
  color: #fff;
  background-color: #FF6B6B;
  box-shadow: 2px 2px 2px 2px rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);

}
</style>
