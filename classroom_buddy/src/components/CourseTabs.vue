<template>
    <div>
        <span class="tab" v-for="(tab, index) in tabs"
        v-bind:key="index"
        v-on:click="selectTab(tab)"
        v-bind:class="{ activeTab: selectedTab === tab }">
        {{ tab }}
        </span>
        <hr class="tab-separator">
        <div class="reviews-section" v-show="selectedTab == 'Reviews'">
            <p v-if="reviews.length === 0">
                No reviews yet.
            </p>
            <ol v-else>
                <li :key="review.name" v-for="review in reviews">
                   {{ review.name }}: {{ review.message }} ({{ review.rating }}/5)
                </li>
            </ol>
        </div>
        <div v-show="selectedTab === 'Give review'">
            <CourseReview @message-submitted="addMessage"/> </div>
        </div>
</template>

<script>
import CourseReview from './CourseReview.vue'

export default {
  components: { CourseReview },
  data () {
    return {
      selectedTab: 'Reviews',
      reviews: [],
      tabs: ['Reviews', 'Give review'] }
  },
  methods: {
    addMessage (courseReview) {
      this.reviews.push(courseReview)
      let sumRating = 0
      for (var i = 0; i < this.reviews.length; i++) {
        sumRating += this.reviews[i].rating
      }
      let avgRating = sumRating / this.reviews.length
      this.$emit('get-avg-feedback', avgRating)
    },
    selectTab (tab) { this.selectedTab = tab } }
}
</script>

<style>

</style>
