<template>
  <div>
    <h1>Hello world</h1>
    <p>This should show up properly!</p>
    <ul>
      <li>test</li>
      <li>test2</li>
    </ul>
    {{ exresponse }}
  </div>
</template>

<script>
import json from "./testFiles/exampleResponse.json";

export default {
  name: "App",
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


