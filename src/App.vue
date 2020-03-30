<template>
  <div id="app">
    <div id="links">
      <router-link to='/'>Home</router-link> |
      <router-link to='/users'>Users</router-link>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>

export default {
  name: 'App'
  
}
</script>

<style>
#links{
  text-align: center;
}
</style>
