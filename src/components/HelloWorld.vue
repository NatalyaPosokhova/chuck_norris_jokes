<template>
  <div class="hello">
    <h1>Chuck Norris Jokes</h1>
    <input readonly type="text" v-model="text" />
    <button @click="GetJokeMethod()">Get Joke</button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      text: "Here will be a Joke, just press the button 'Get Joke'"
    };
  },

  methods: {
    GetJokeMethod: function() {
      fetch("https://api.chucknorris.io/jokes/random")
        .then(response => response.json())
        .then(data => {
          //console.log(data);
          const text = data.value;
          this.text = text;
        })
        .catch(error => console.error(error));
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  font-family: Cambria, Cochin, Georgia, Times, "Times New Roman", serif;
}
h1 {
  font-weight: bold;
}
input {
  width: 60%;
  padding: 12px 24px;
  margin: 4px 2px;
  background-color: lightpink;
  border: none;
  font-size: 14px;
}
button {
  width: 10%;
  padding: 10px 30px;
  text-align: center;
  font-size: 16px;
  color: lightskyblue;
}
</style>
