<template>
  <div id="app">
    <div class="course-container">
      <div class="header">
        <span class="brand">Classroom Buddy</span>
        <div class="total-enrollments" title="Your enrollments">
          {{ currentEnrollments }}
        </div>
      </div>
      <Course :limit="enrollmentsLimit"/>
    </div>
  </div>
</template>

<script>
import Course from './components/Course.vue'

export default {
  components: { Course },
  name: 'App',
  data () {
    return {
      enrollmentsLimit: 50,
      currentEnrollments: 0
    }
  },
  methods: {
    enroll () {
      this.enrollmentStatus = 'Enrolled'
      this.currentEnrollments += 1
    },
    enrollOver () {
      console.log('over BTN')
    },
    enrollLeave () {
      console.log('not over BTN')
    },
    cancel () {
      this.enrollmentStatus = 'Fresh'
      this.currentEnrollments -= 1
    }
  }
}
</script>

<style>
body {
  margin: 0px;
}

.header {
  background: linear-gradient(to right, #9ED6E8 , #AEE7E8);
  padding: 10px;
  margin-bottom: 15px;
}

.brand {
  font-weight: bold;
  font-size: 1.5em;
}

.total-enrollments {
  width: 25%;
  float: right;
  text-align: right;
  padding-right: 2%;
  padding-top: 0.2%;
}

.course {
  display: inline-block;
  margin: 10px 20px;
  border: #5A0A70 1px solid;
  border-radius: 7px 0px;
  padding: 20px;
}

.course-main {
  background: linear-gradient(to bottom right, #B582E8, #DDABEB);
  border-top-left-radius: 5px;
}

.course-title {
  padding: 15px 0px;
  text-align: center;
  font-size: 1.5em;
  font-family: serif;
}

.prerequisites {
  margin: 0px 0px 0px 3%;
}

.prerequisite-list {
  margin: 10px 0px 0px 0px;
  list-style-type: circle;
  padding-bottom: 10px;
}

.details {
  height: 25px;
  margin-top: 15px;
  margin-bottom: 15px;
}

.enrollment-info {
  padding: 2px 0px 0px 10px;
  font-size: 1.2em;
  min-width: 100px;
}

.enrollment-bar {
  display: flex;
  flex-wrap: wrap;
}

.course-button {
  padding: 5.2%;
  text-align: right;
}

.action-button {
  border-color: transparent;
  border-radius: 2px;
  margin-left: auto;
  margin-right: 10px;
  height: 25px;
  box-shadow: 0 5px 5px rgba(0, 0, 0, 0.25), 0 5px 5px rgba(0, 0, 0, 0.22);
}

.enroll {
  background: yellowgreen;
}

.cancel {
  background: tomato;
}
</style>
