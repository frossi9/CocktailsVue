<template>
  <div>
    <h1> List of Beers </h1>
    <div v-for="(beer, i) in beers" :key="i">
      <h2> {{ beer.name}}</h2>
      <p> {{ beer.description }} </p> 
      <ul> 
        <li> {{ beer.food_pairing[0]}} </li>
        <li> {{beer.food_pairing[1]}}</li>
        <li> {{beer.food_pairing[2]}} </li> 
      </ul> 

    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      beers: {}
    };
  },
  mounted: async function () {
        const url= "https://api.punkapi.com/v2/beers";
        const response = await fetch(url);
        const result = await response.json();
        this.beers = result; 
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
