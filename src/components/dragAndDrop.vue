<template>
  <div>
    <!--UPLOAD-->
    <div id="descriptionText">
      <p>
        Upload your resume in PDF or docx file in order to see <br />
        how it would get parsed by top companies
      </p>
    </div>
    <div id="dragdrop" @dragover.prevent @drop.prevent>
      <div
        class="container"
        @drop="handleFileDrop"
        @click="this.$refs.upload.click()"
      >
        <!-- <p>Add your files here:</p> -->
        <input
          ref="upload"
          type="file"
          name="file-upload"
          @change="onUploadFiles"
          hidden
        />
      </div>
    </div>
    <parsedResume :jsonResponse="jsonResponse"></parsedResume>
  </div>
</template>

<!-- Javascript -->
<script>
import parsedResume from "./parsedResume";
export default {
  components: { parsedResume },
  data: function () {
    return {
      files: [],
      jsonResponse: "",
    };
  },
  methods: {
    handleFileDrop(e) {
      let droppedFiles = e.dataTransfer.files;
      if (!droppedFiles) return;
      // this tip, convert FileList to array, credit: https://www.smashingmagazine.com/2018/01/drag-drop-file-uploader-vanilla-js/
      [...droppedFiles].forEach((f) => {
        this.files.push(f);
      });
      let formdata = new FormData();
      formdata.append("resume", this.files[0], this.files[0].name);
      this.apiRequest(formdata);
      this.files = [];
    },
    onUploadFiles() {
      console.log(this.$refs.upload.files[0]);
      let formdata = new FormData();
      formdata.append(
        "resume",
        this.$refs.upload.files[0],
        this.$refs.upload.files[0].name
      );
      this.$refs.upload.value = "";
      this.apiRequest(formdata);
    },
    apiRequest(formdata) {
      var requestOptions = {
        method: "POST",
        body: formdata,
        redirect: "follow",
        mode: "cors",
      };

      let proxyCORS = "https://cors-anywhere.herokuapp.com/";
      let targetURL = "https://jobs.lever.co/parseResume";
      fetch(proxyCORS + targetURL, requestOptions)
        .then((response) => response.json())
        .then((result) => {
          console.log(result);
          this.jsonResponse = result;
        })
        .catch((error) => console.log("error", error));
    },
  },
};
</script>

<style scoped>
.container {
  box-sizing: border-box;
  width: 40%;
  height: 20em;
  background-color: #f3faff;
  border: 3px dashed lightskyblue;
  padding: 50px;
  border-radius: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-image: url("../assets/upload.png");
  background-repeat: no-repeat;
  background-position: center center;
  background-size: 60% auto;
  min-width: 500px;
}

#dragdrop {
  display: flex;
  justify-content: center;
  margin: 10px;
}

#descriptionText {
  display: flex;
  justify-content: center;
}

p {
  text-align: center;
  font-size: 1.2rem;
}
</style>