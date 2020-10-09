<template>
  <div>
    <h1>OTHER PAGES</h1>
    <h1>INPUT - UPLOAD A FILE</h1>
    <h1>SHOW THE PARSED RESULTS</h1>
    <HelloWorld></HelloWorld>
  </div>
</template>

<script>
import json from "./testFiles/exampleResponse.json";
import HelloWorld from "./components/HelloWorld";
export default {
  name: "App",
  components: {
    HelloWorld,
  },
  data: function () {
    return {
      exresponse: json,
    };
  },
};
</script>

<style scoped>
p {
  background-color: lightblue;
}

li {
  list-style: none;
  display: inline-block;
  margin: 10px;
  background-color: greenyellow;
}
</style>


