<template>
  <div id="theSortingHat" class="unsorted">
    <div class="card">
      <h1>{{ house ? house: "Welcome to Hogwarts" }}</h1>
      <button @click="getHouse()">Sort!</button>
    </div>
  </div>
</template>

<script>
const axios = require('axios');

export default {
  name: "SortingHat",
  data()  {
    return {
      house: ""
    }
  },
  methods: {
    getHouse: function () {
      axios.get('https://www.potterapi.com/v1/sortingHat')
        .then((response) => {
          this.house = response.data;
          return response.data;
        }).then((response) =>{
          document.getElementById("theSortingHat").className = response.toLowerCase()
        })
        .catch(function(error){
          // eslint-disable-next-line
          console.log(error)
        })
    }
  }
}
</script>

<style scoped>

.unsorted {
  --primary: #000000;
  --secondary: #ffffff;
}

.ravenclaw {
  --primary: #242F5C;
  --secondary: #CD7F32;
}

.gryffindor {
  --primary: #740001;
  --secondary: #D3A625;
}

.slytherin {
  --primary: #2A623D;
  --secondary: #ffffff;
}

.hufflepuff {
  --primary: #FFDB00;
  --secondary: #000000;
}

button {
  color: var(--primary);
  background-color: var(--secondary);
  border: 1px solid var(--primary);
  line-height: 1.5rem;
  padding: 5px 45px;
  font-weight: bold;
  font-size: 1.3rem
}

h1 {
  color: var(--secondary);
}
.card {
  width: 50vw;
  margin: auto;
  background-color: var(--primary);
  border: 2px solid var(--secondary);
  padding: 2rem 2rem;
  border-radius: 7px;
  box-shadow: 5px 5px 7px var(--primary)
}
</style>

