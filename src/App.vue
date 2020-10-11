<template>
  <div>
    <h1>OTHER PAGES</h1>
    <h1>INPUT - UPLOAD A FILE</h1>
    <h1>SHOW THE PARSED RESULTS</h1>
    <input
      ref="upload"
      type="file"
      name="file-upload"
      @change="onUploadFiles"
    />
  </div>
</template>

<script>
import json from "./testFiles/exampleResponse.json";

export default {
  name: "App",
  components: {},
  data: function () {
    return {
      exresponse: json,
    };
  },
  methods: {
    onUploadFiles() {
      console.log(this.$refs.upload.files[0]);
      var formdata = new FormData();
      formdata.append(
        "resume",
        this.$refs.upload.files[0],
        this.$refs.upload.files[0].name
      );

      var requestOptions = {
        method: "POST",
        body: formdata,
        redirect: "follow",
        mode: "cors",
      };

      let proxyCORS = "https://cors-anywhere.herokuapp.com/";
      let targetURL = "https://jobs.lever.co/parseResume";
      fetch(proxyCORS + targetURL, requestOptions)
        .then((response) => response.text())
        .then((result) => console.log(result))
        .catch((error) => console.log("error", error));
    },
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


