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
            </div>
        </div>
        <hr>
        <p class="feedback-bar">
          <span title="Average Feedback">
            Feedback: {{ avgFeedback }}
          </span>
          <span v-if="feedbackOpen" class="feedback-view" v-on:click="feedbackSection(false)">Hide Feedback</span>
          <span v-else class="feedback-view" v-on:click="feedbackSection(true)">View Feedback</span> </p>
          <div class="feedback-div" v-show="feedbackOpen">
            <CourseTabs @get-avg-feedback="setAvgFeedback"/>
          </div>
    </div>
</template>

<script>
import CourseTabs from './CourseTabs.vue'

export default {
  components: { CourseTabs },
  name: 'Course',
  data () {
    return {
      name: 'Vue JS',
      currentEnrollments: 0,
      description: 'A basic course to understand the concepts of Vue JS',
      enrollmentStatus: 'Fresh',
      prerequisites: ['HTML', 'CSS', 'JS'],
      mouseOnCourse: false,
      reviews: [],
      feedbackOpen: false,
      avgFeedback: 'NA'
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
    },
    addMsg (courseReview) {
      this.reviews.push(courseReview)
    },
    feedbackSection (shouldOpen) {
      this.feedbackOpen = shouldOpen
    }
  },
  computed: {
    enrollmentStats () {
      return (this.currentEnrollments + '/' + this.limit)
    },
    setAvgFeedback () {
      if (this.reviews.length === 0) {
        return 'N/A'
      }
      let sum = 0

      this.reviews.forEach(review => {
        sum += review.rating
      })
      return (sum / this.reviews.length).toFixed(2) + '/5'
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
