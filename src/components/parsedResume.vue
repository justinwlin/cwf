<template>
  <div class="page">
    <button> button </button>
    <span v-if="jsonResponse">
<<<<<<< HEAD
      <b>Name:</b>
      {{ name }}
      <br />
      <b>Years of experience:</b>
      {{ yoe }}
=======
 
>>>>>>> b8880b913d50d154c48eb462926b4082170d103a
      <br />
      <b>Phone:</b>
      {{ phone }}
      <br />
      <b>Email:</b>
      {{ email }}
      <!-- <br /><b>Location: </b>
    {{ location }}-->
      <h1>Education</h1>
      <b>{{ school }}</b>
      <br />
      <b>Start:</b>
      {{ school_start }}
      <br />
      <b>End:</b>
      {{ school_end }}
      <br />
      <b>Major:</b>
      {{ major }}
      <br />
      <b>GPA:</b>
      {{ GPA }}
      <br />
      <h1>Experience</h1>
      <br />
      <div v-for="position in positions" :key="position.title">
        <h1>{{ position.title }}</h1>
        <h2>{{ position.org }}</h2>
        <b>Start:</b>
        {{ position.start.month }}
        {{ position.start.year }}
        <br />
        <b>End:</b>
        {{ position.isCurrent ? "Current Position" : position.end.year }}
        <p>{{ position.summary }}</p>
      </div>

      <h1>Skills</h1>
      <b>Skills:</b>
      {{ skills }}
    </span>
  </div>
</template>

<script>
// import json from "../testFiles/ophelia.json";
export default {
  name: "parsedResume",
  props: ["jsonResponse"],
  data: function () {
    return {};
  },
  computed: {
    summary() {
      if (this.jsonResponse == "") {
        return "";
      }
      try {
        return this.jsonResponse.summary.experience
          ? this.jsonResponse.summary.experience
          : "XXX";
      } catch {
        return "";
      }
    },
    name() {
      if (this.jsonResponse == "") {
        return "";
      }
      try {
        return this.jsonResponse.names[0] ? this.jsonResponse.names[0] : "XXX";
      } catch {
        return "";
      }
    },
    yoe() {
      if (this.jsonResponse == "") {
        return "";
      }
      try {
        return this.jsonResponse.summary.workTime.years
          ? this.jsonResponse.summary.workTime.years
          : "N/A";
      } catch {
        return "";
      }
    },
    email() {
      if (this.jsonResponse == "") {
        return "";
      }
      try {
        return this.jsonResponse.emails[0].value
          ? this.jsonResponse.emails[0].value
          : "N/A";
      } catch {
        return "";
      }
    },
    phone() {
      if (this.jsonResponse == "") {
        return "";
      }
      try {
        return this.jsonResponse.phones[0].value
          ? this.jsonResponse.phones[0].value
          : "N/A";
      } catch {
        return "";
      }
    },
    location() {
      if (this.jsonResponse == "") {
        return "";
      }
      try {
        if (this.jsonResponse.has("location")) {
          return this.jsonResponse.location.name
            ? this.jsonResponse.location.name
            : "N/A";
        }
      } catch {
        return "";
      }
      return "";
    },
    skills() {
      if (this.jsonResponse == "") {
        return "";
      }
      try {
        return this.jsonResponse.summary.skills
          ? this.jsonResponse.summary.skills
          : "N/A";
      } catch {
        return "";
      }
    },
    school() {
      if (this.jsonResponse == "") {
        return "";
      }
      try {
        return this.jsonResponse.schools[0].org
          ? this.jsonResponse.schools[0].org
          : "N/A";
      } catch {
        return "";
      }
    },
    school_start() {
      if (this.jsonResponse == "") {
        return "";
      }
      try {
        return this.jsonResponse.schools[0].start.year
          ? this.jsonResponse.schools[0].start.year
          : "N/A";
      } catch {
        return "";
      }
    },
    school_end() {
      if (this.jsonResponse == "") {
        return "";
      }
      return this.jsonResponse.schools[0].end.year
        ? this.jsonResponse.schools[0].end.year
        : "N/A";
    },
    GPA() {
      if (this.jsonResponse == "") {
        return "";
      }
      try {
        return this.jsonResponse.schools[0].gpa
          ? this.jsonResponse.schools[0].gpa
          : "N/A";
      } catch {
        return "";
      }
    },
    major() {
      if (this.jsonResponse == "") {
        return "";
      }

      try {
        return this.jsonResponse.schools[0].field
          ? this.jsonResponse.schools[0].field
          : "N/A";
      } catch {
        return "";
      }
    },

    positions() {
      if (this.jsonResponse == "") {
        return "";
      }
      try {
        return this.jsonResponse.positions;
      } catch {
        return "";
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.page {
  width: 75%;
  max-width: 800px;
  min-width: 500px;
  margin: 0 auto;
  /* border: 1px solid black; */
  padding: 20px;
  box-shadow: 0px 24px 32px rgba(0, 0, 0, 0.04),
    0px 16px 24px rgba(0, 0, 0, 0.04), 0px 4px 8px rgba(0, 0, 0, 0.04),
    0px 0px 1px rgba(0, 0, 0, 0.04);
}
</style>
