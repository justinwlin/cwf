<template>
  <div id="header">
    <span> <img class="headerIcon" src="../assets/smartparser.png" /> </span>
    <span id="rightHeader">
      <img class="headerIcon" src="../assets/github.png" />
      <img class="headerIcon" src="../assets/info.png" />
      <img class="headerIcon" src="../assets/cwfLogo.png" />
    </span>
  </div>
</template>

<script>
export default {
  name: "HeaderCWF",
  props: {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #e5e5e5;
}

#rightHeader {
  display: flex;
  align-items: center;
}

.headerIcon {
  margin: 0px 10px;
}
</style>
