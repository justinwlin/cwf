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
    <br /><b>Start: </b>
    {{ school_start }}
    <br /><b>End: </b>
    {{ school_end }}
    <br /><b>Major: </b>
    {{ major }}
    <br /><b>GPA: </b>
    {{ GPA }}
    <br />
    <h1>Experience</h1>

    <br /><b>Position: </b>
    <div v-for="position in positions" :key="position.title">
      <h1>{{ position.title }}</h1>
      <h2>{{ position.org }}</h2>
      <p>{{ position.summary }}</p>
    </div>
    <h1>Skills</h1>
  </div>
</template>

<script>
import json from "../testFiles/ophelia.json";
export default {
  name: "parsedResume",
  data: function() {
    return {
      parsedResume: json
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
        : "N/A";
    },
    email() {
      return this.parsedResume.emails[0].value
        ? this.parsedResume.emails[0].value
        : "N/A";
    },
    phone() {
      return this.parsedResume.phones[0].value
        ? this.parsedResume.phones[0].value
        : "N/A";
    },
    location() {
      if (this.parsedResume.has("location")) {
        return this.parsedResume.location.name
          ? this.parsedResume.location.name
          : "N/A";
      }
      return "N/A";
    },
    skills() {
      return this.parsedResume.summary.skills
        ? this.parsedResume.summary.skills
        : "N/A";
    },
    school() {
      return this.parsedResume.schools[0].org
        ? this.parsedResume.schools[0].org
        : "N/A";
    },
    school_start() {
      return this.parsedResume.schools[0].start.year
        ? this.parsedResume.schools[0].start.year
        : "N/A";
    },
    school_end() {
      return this.parsedResume.schools[0].end.year
        ? this.parsedResume.schools[0].end.year
        : "N/A";
    },
    GPA() {
      return this.parsedResume.schools[0].gpa
        ? this.parsedResume.schools[0].gpa
        : "N/A";
    },
    major() {
      return this.parsedResume.schools[0].field
        ? this.parsedResume.schools[0].field
        : "N/A";
    },
    positions() {
      return this.parsedResume.positions;
    }
  }
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
