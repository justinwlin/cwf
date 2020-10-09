<template>
  <div>
    <HelloWorld></HelloWorld>
    <HelloWorld />
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


