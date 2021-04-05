<template>
    <div>
        <form @submit.prevent="onSubmit" class="review-form">
            <div class="error-section" v-show="errorState">
                <p>Warning!!!</p>
                    <ul class="error-list">
                        <li v-show="name == null">Provide Name</li>
                        <li v-show="message == null">Provide Feedback</li>
                        <li v-show="rating == null || rating === 0">Provide Rating</li>
                    </ul>
            </div>
            <div class="review-div">
                <label for="name">
                    Name:
                </label>
                <br>
                <input class="review-input" v-model="name" id="name" placeholder="Enter Name">
            </div>
            <div class="review-div">
                <label for="message">
                    Feedback:
                </label>
                <br>
                <input class="review-input message-area" v-model="message" id="message" placeholder="Enter Feedback">
            </div>
            <div class="review-div">
                <label for="rating">
                    Rating:
                </label>
                <br>
                <select class="review-select review-input" id="rating" v-model.number="rating">
                    <option value="0" disabled selected>Please Rate</option>
                    <option value="5">5</option>
                    <option value="4">4</option>
                    <option value="3">3</option>
                    <option value="2">2</option>
                    <option value="1">1</option>
                </select>
            </div>
            <div class="review-div">
                <input class="review-submit" type="Submit">
            </div>
        </form>
    </div>
</template>

<script>
export default {
  data () {
    return {
      name: null,
      message: null,
      rating: 0,
      errorState: false
    }
  },
  methods: {
    onSubmit () {
      this.errorState = (this.name == null) || (this.message == null) || (this.rating == null) || (this.rating === 0)

      if (!this.errorState) {
        let courseReview = {
          name: this.name,
          message: this.message,
          rating: this.rating
        }

        this.$emit('msg-submitted', courseReview)
        //   console.log(courseReview.name + ' ' + courseReview.message + ' ' + courseReview.rating)
        this.name = null
        this.message = null
        this.rating = null
      }
    }
  }
}
</script>

<style scoped>

</style>
