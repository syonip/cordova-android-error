<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    {{ response }}
  </div>
</template>

<script>
const axios = require("axios");
export default {
  name: "HelloWorld",
  data() {
    return {
      response: ''
    }
  },
  props: {
    msg: String
  },
  mounted() {
    document.addEventListener(
      typeof cordova !== "undefined" ? "deviceready" : "DOMContentLoaded",
      () => {
        axios
          .get("/test.csv")
          .then(response => {
            this.response = response;
          })
          .catch(err => {
            this.response = `ERROR!
             ${err}`;
          });
      }
    );
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
