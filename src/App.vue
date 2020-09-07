<template>
  <div id="app" class="container">
  <h1>Weather website</h1>
  <div id="search" class="card px-5 py-5">
  <input type="text" name="search" 
  placeholder="Search the weather" class="form-control mb-3">
  <button class="btn btn-primary">Search</button>
  </div>
  <div id="weather">
    <h2>Weather info</h2>
    <table class="table table-bordered table-striped">
      <tr>
        <th>Date time</th>
        <th>Weather</th>
        <th>Temperature</th>
        <th>Icon</th>
      </tr>
    </table>
  </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
