<template>
  <div class="hello">
    <h1>View Parsed Resume</h1>
    <h1>Summary</h1>
    {{ summary }}
    <h1>Basic Info</h1>
    <b>Name: </b>
    {{ name }}
    <br /><b>Years of experience: </b>
    {{ yoe }}
    <!-- <br /><b>Phone: </b>
    {{ phone }} -->
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
      return this.parsedResume;
    },
    location() {
      if (this.parsedResume.has("location")) {
        return this.parsedResume.location.name;
      }
      return "N/A";
    },
    skills() {
      return this.parsedResume.summary.skills;
    },
    school() {
      return this.parsedResume.schools[0].org;
    },
    // GPA(){
    //   if (json.has("")
    // },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
