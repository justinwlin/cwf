<template>
  <div class="page">
    <h1>View Parsed Resume</h1>
    <h1>Summary</h1>
    {{ summary }}
    <h1>Basic Info</h1>
    <b>Name: </b>
    {{ name }}
    <br /><b>Years of experience: </b>
    {{ yoe }}
    <br /><b>Phone: </b>
    {{ phone }}
    <br /><b>Email: </b>
    {{ email }}
    <!-- <br /><b>Location: </b>
    {{ location }} -->
    <h1>Education</h1>
    <b>{{ school }}</b>
    <h1>Experience</h1>
    <h1>Skills</h1>
  </div>
</template>
∂
<script>
import json from "../testFiles/ophelia.json";
export default {
  name: "parsedResume",
  data: function () {
    return {
      parsedResume: json,
    };
  },
  computed: {
    summary() {
      return this.parsedResume.summary.experience
        ? this.parsedResume.summary.experience
        : "XXX";
    },
    name() {
      return this.parsedResume.names[0] ? this.parsedResume.names[0] : "XXX";
    },
    yoe() {
      return this.parsedResume.summary.workTime.years
        ? this.parsedResume.summary.workTime.years
        : "XXX";
    },
    email() {
      return this.parsedResume.emails[0].value
        ? this.parsedResume.emails[0].value
        : "XXX";
    },
    phone() {
      return this.parsedResume.phones[0].value;
    },
    location() {
      if (this.parsedResume.has("location")) {
        return this.parsedResume.location.name
          ? this.parsedResume.summary.experience
          : "XXX";
      }
      return "N/A";
    },
    skills() {
      return this.parsedResume.summary.skills
        ? this.parsedResume.summary.experience
        : "XXX";
    },
    school() {
      return this.parsedResume.schools[0].org
        ? this.parsedResume.summary.experience
        : "XXX";
    },
    // GPA(){
    //   if (json.has("")
    // },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.page {
  width: 75%;
  max-width: 800px;
  margin: 0 auto;
  border: 1px solid black;
  padding: 20px;
}
</style>
