<template>
<!-- HI -->
  <div id="appContent">
    <HeaderCWF></HeaderCWF>
    <h1>INPUT - UPLOAD A FILE</h1>
    <input
      ref="upload"
      type="file"
      name="file-upload"
      @change="onUploadFiles"
    />
    <h1>SHOW THE PARSED RESULTS</h1>
  </div>
</template>

<script>
import json from "./testFiles/exampleResponse.json";
import HeaderCWF from "./components/HeaderCWF";

export default {
  name: "App",
  components: { HeaderCWF },
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

<style>
/* Resetting styles */
html,
body {
  margin: 0;
  padding: 0;
}

#appContent {
  height: 100vh;
  background-image: url("./assets/footer.png");
  background-repeat: no-repeat;
  background-position: center bottom;
  background-size: 100% auto;
}
</style>


