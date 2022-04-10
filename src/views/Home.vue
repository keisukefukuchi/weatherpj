<template>
  <div class="home flex">
    <Card v-for="(data,index) in lists" :key="index" :city="data.city" :img="data.img"></Card>
  </div>
</template>
<script>
import Card from "../components/Card";
export default {
  data() {
    return {
      lists: [
        {
          city: "sapporo",
          img: "Hokkaido"
        },
        {
          city: "tokyo",
          img: "Tokyo"
        },
        {
          city: "nagoya",
          img: "Aichi"
        },
        {
          city: "osaka",
          img: "Osaka"
        },
        {
          city: "fukuoka",
          img: "Fukuoka"
        },
        {
          city: "naha",
          img: "Okinawa"
        }
      ]
    };
  },
  components: {
    Card
  }
};
</script>

<style scoped>
body {
  background: #eee;
}
.flex {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  
}
</style>
