<template>
  <div class="about">
    <div class="weather">
      <h1 class="weather-title">{{city}}の天気情報</h1>
      <ul>
        <li>天気 : {{main}}</li>
        <li>温度 : {{temp}}℃</li>
        <li>湿度 : {{humidity}}%</li>
        <li>風速 : {{ speed }}m</li>
      </ul>
      <a @click="$router.push({name:'Home'})" class="cp_btn">
        戻る
      </a>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  props:["city"],
  data() {
    return {
      name: "",
      main: "",
      temp: "",
      humidity: "",
      speed: ""
    };
  },
  async created() {
    const item = await axios.get(
      `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=717bb5ec02fc2678f4c115b11c61b291`
    );
    const weatherData = item.data;
    this.name = weatherData.name;
    this.main = weatherData.weather[0].main;
    this.temp = weatherData.main.temp;
    this.humidity = weatherData.main.humidity;
    this.speed = weatherData.wind.speed;
  }
};
</script>

<style scoped>
.about {
  width: 100vw;
  height: 100vh;
  background: url("../assets/weather.jpg")
    no-repeat;
  background-size: cover;
  color: white;
}
.weather {
  width: 620px;
  margin: 0 auto;
  padding-top: 100px;
}
.weather-title {
  font-size: 64px;
}
.weather li {
  font-size: 24px;
  margin-top: 20px;
  margin-left: 30px;
}
.cp_btn {
  display: block;
  width: 600px;
  margin-top: 50px;
  padding: 10px;
  text-align: center;
  text-decoration: none;
  color: #ec407a;
  border: 2px solid #ec407a;
  border-radius: 3px;
  transition: 0.4s;
  cursor: pointer;
}
.cp_btn:hover {
  background: #ec407a;
  color: #fff;
}
</style>
