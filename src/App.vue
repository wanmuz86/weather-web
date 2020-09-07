<template>
  <div id="app" class="container">
    <h1>Weather website</h1>
    <div id="search" class="card px-5 py-5">
      <input type="text" name="search" 
      placeholder="Search the weather" class="form-control mb-3" v-model="searchedCity">
      <button class="btn btn-primary" v-on:click="searchWeather">Search</button>
    </div>
    <div id="weather" v-if="weathers.length != 0">
      <h2>Weather info</h2>
      <h3>{{city}}</h3>
      <table class="table table-bordered table-striped">
        <tr>
          <th>Date time</th>
          <th>Weather</th>
          <th>Temperature</th>
          <th>Icon</th>
        </tr>
        <tr v-for="weather in weathers" :key="weather.dt" v-on:click="selectWeather(weather)">
          <td>{{new Date(weather.dt*1000)}}</td>
          <td>{{weather.weather[0].main}}</td>
          <td>{{(weather.temp.day - 273.15).toFixed(2)}} C</td>
          <td><img v-bind:src="`https://openweathermap.org/img/wn/${weather.weather[0].icon}@2x.png`"></td>
        </tr>
      </table>
    </div>
    <div id="detail" class="card px-5 py-5" v-if="selectedWeather">
      <p><img v-bind:src="`https://openweathermap.org/img/wn/${selectedWeather.weather[0].icon}@2x.png`"/></p>
      <p>{{new Date(selectedWeather.dt*1000)}}</p>
    </div>
  </div>
</template>
<script>

  export default {
    name: 'App',
    data() {
      return {
      weathers: [],
      city: null,
      searchedCity:'',
      selectedWeather:null
    }
    },
    methods: {
      selectWeather: function(weather){
        console.log(weather)
        this.selectedWeather = weather;
      },
      searchWeather: function(){
        fetch('https://api.openweathermap.org/data/2.5/forecast/daily?q='+this.searchedCity+'&appid=9fd7a449d055dba26a982a3220f32aa2')
        .then(response => response.json())
        .then(data => {
          console.log('Success:', data);
          this.weathers = data["list"]
          this.city = data.city.name
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
