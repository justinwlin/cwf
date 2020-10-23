<template>
  <div>
    <!--UPLOAD-->
    <h1>Upload images</h1>
    <div id="app" @dragover.prevent @drop.prevent>
      <div class="container" @drop="handleFileDrop">
        Add your files here:
        <br />
        <input
          ref="upload"
          type="file"
          name="file-upload"
          @change="onUploadFiles"
        />
        <ul></ul>
      </div>
    </div>
  </div>
</template>

<!-- Javascript -->
<script>
export default {
  name: "dragAndDrop",
  props: {},
  data: function () {
    return {
      files: [],
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
      this.files = 0;
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
          return result;
        })
        .catch((error) => console.log("error", error));
    },
  },
};
</script>

<style scoped>
.container {
  background-color: blue;
  height: 50px;
}
</style>