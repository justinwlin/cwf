<template>
  <div class="hello">
    <h1>View Parsed Resume</h1>
    <h1>Summary</h1>
    {{ summary }}
    <h1>Basic Info</h1>
    <b>Name: </b>
    {{ name }}
    <br/><b>Years of experience: </b>
    {{ yoe }}
    <br/><b>Phone: </b>
    <br/><b>Email: </b>
    <br/><b>Location: </b>
    <h1>Education</h1>
    <h1>Experience</h1>
    <h1>Skills</h1>
  </div>
</template>
∂
<script>
import json from "../testFiles/exampleResponse.json";
export default {
  name: "parsedResume",
  data: function () {
    return {
      parsedResume: json,
    };
  },
  computed: {
    summary() {
      return this.parsedResume.summary.experience;
    },
    name() {
      return this.parsedResume.names[0];
    },
    yoe() {
      return this.parsedResume.summary.workTime.years;
    },
    email() {
      return this.parsedResume.emails[0].value;
    },
    phone() {
      if (json.has("phones")) {
        return this.parsedResume.phones[0].value;
      }
      return "N/A";
    },
    location() {
      if (json.has("location")) {
        return this.parsedResume.location.name;
      }
      return "N/A";
    },
    skills() {
      return this.parsedResume.summary.skills;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
