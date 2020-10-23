<template>
  <!-- HI -->
  <div id="appContent">
    <HeaderCWF></HeaderCWF>
    <div id="orangeLogo">
      <img src="./assets/orangeLogo.png" />
    </div>
    <dragAndDrop></dragAndDrop>
    <!-- <input
      ref="upload"
      type="file"
      name="file-upload"
      @change="onUploadFiles"
    /> -->
    <parsedResume></parsedResume>
  </div>
</template>

<script>
import HeaderCWF from "./components/HeaderCWF";
import parsedResume from "./components/parsedResume";
import dragAndDrop from "./components/dragAndDrop";
export default {
  name: "App",
  components: { HeaderCWF, parsedResume, dragAndDrop },
  data: function () {
    return {};
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
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@300&display=swap");

/* Resetting styles */
html,
body,
p {
  margin: 0;
  padding: 0;
  font-family: "Montserrat";
}

#orangeLogo {
  display: flex;
  justify-content: center;
}

/* #appContent {
  height: 100vh;
  background-image: url("./assets/footer.png");
  background-repeat: no-repeat;
  background-position: center bottom;
  background-size: 100% auto;
} */
</style>


