<template>
  <div id="app" class="container">
    <h1>Weather website</h1>
    <div id="search" class="card px-5 py-5">
      <input type="text" name="search" 
      placeholder="Search the weather" class="form-control mb-3">
      <button class="btn btn-primary" v-on:click="searchWeather">Search</button>
    </div>
    <div id="weather">
      <h2>Weather info</h2>
      <table class="table table-bordered table-striped">
        <tr>
          <th>Date time</th>xx
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
    data() {
      return {
      weathers: []
    }
    },
    methods: {
      searchWeather: function(){
        fetch('https://api.openweathermap.org/data/2.5/forecast/daily?q=Kuala%20Lumpur&appid=9fd7a449d055dba26a982a3220f32aa2')
        .then(response => response.json())
        .then(data => {
          console.log('Success:', data);
          this.weathers = data["list"]
        })
        .catch((error) => {
          console.error('Error:', error);
        });
      }
    }

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
