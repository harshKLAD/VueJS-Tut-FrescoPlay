<template>
    <div class="course" @mouseover="highlight_enroll()" @mouseleave="dehighlight_enroll()">
        <div class="course-main">
            <div class="course-title" v-bind:title="description">
                {{ name }}
            </div>
            <div>
                <p class="prerequisites">Prerequisites</p>
                <ul>
                    <li v-for="ele in prerequisites" v-bind:key="ele">{{ ele }}</li>
                </ul>
            </div>
        </div>
        <div class="details">
            <div class="enrollment-bar">
                <div class="enrollment-info" title="Course Enrollments">
                {{ enrollmentStats }}
                </div>
                <button class="action-button enroll" :class="{ 'enroll-hover': mouseOnCourse }" v-if="enrollmentStatus == 'Fresh'" v-on:click="enroll()">
                    Enroll
                </button>
                <button class="action-button cancel" v-else-if="enrollmentStatus == 'Enrolled'" v-on:click="cancel()">
                    Cancel
                </button>
                <span v-else>Enrolled</span>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'Course',
  data () {
    return {
      name: 'Vue JS',
      currentEnrollments: 0,
      description: 'A basic course to understand the concepts of Vue JS',
      enrollmentStatus: 'Fresh',
      prerequisites: ['HTML', 'CSS', 'JS'],
      mouseOnCourse: false
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
    },
    highlight_enroll () {
      this.mouseOnCourse = true
    },
    dehighlight_enroll () {
      this.mouseOnCourse = false
    }
  },
  computed: {
    enrollmentStats () {
      return (this.currentEnrollments + '/' + this.limit)
    }
  },
  props: {
    limit: {
      type: Number,
      required: true,
      default: 20
    }
  }
}
</script>

<style scoped>

</style>
