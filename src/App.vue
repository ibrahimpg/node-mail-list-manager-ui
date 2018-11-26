<template>
  <div id="app">
    <router-view/>
    <div id="nav">
      <router-link to="/">Mailing List</router-link>
      <router-link to="/compose">Compose</router-link>
    </div>
  </div>
</template>

<style>

* {
  box-sizing: border-box;
  margin: 0;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  background-color: #42b983;
}

#nav {
  display: flex;
  justify-content: space-around;
  align-items: center;
  background-color: rgba(0,0,0,0.8);
  position: fixed;
  bottom: 0;
  width: 100%;
  height: 50px;
  font-weight: bold;
}

#nav a {
  color: #42b983;
  text-decoration: none;
}

#nav a.router-link-exact-active {
  text-decoration: underline;
}
</style>
