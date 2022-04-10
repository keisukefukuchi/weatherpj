<template>
    <div class="card">
        <img 
        :src="imgSrc"
        alt="" 
        class="card-img"
        >
        <div class="card-content">
            <h1 class="card-title">{{city}}</h1>
        </div>
        <div class="card-link">
            <a @click="$router.push({name:'About',params:{city:city}})">About</a>
        </div>
    </div>
</template>

<script>
export default {
    props:["city","img"],
    computed: {
        imgSrc() {
           return require("../assets/" + this.img + ".jpg")
        },
    },
}
</script>

<style scoped>
.card {
  width: 27%;
  margin: 30px 0;
  background: #fff;
  border-radius: 5px;
  box-shadow: 0 2px 5px #ccc;
}
.card-img {
  width: 100%;
  height: auto;
}
.card-content {
  padding: 20px;
}
.card-title {
  font-size: 20px;
  margin-bottom: 20px;
  text-align: center;
  color: #333;
}
.card-link {
  text-align: center;
  border-top: 1px solid #eee;
  padding: 20px;
}
.card-link a {
  text-decoration: none;
  color: #0bd;
  margin: 0 10px;
  cursor: pointer;
}
.card-link a:hover {
  color: #0090aa;
}
</style>
