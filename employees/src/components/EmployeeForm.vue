<template>
    <div id="employee-form">
        <form v-on:submit.prevent="handlePost(employee)">
            <label for="">Employee ID</label>
            <input v-model="employee.id" type="text" />
            <label for="">Employee Name</label>
            <input v-model="employee.name" type="text" />
            <label for="">Employee Email</label>
            <input v-model="employee.email" type="text" />
            <br>
            <button>Add</button>
        </form>
    </div>
</template>

<script>
export default {
  name: 'employee-form',
  data () {
    return {
      employee: {
        id: '',
        name: '',
        email: ''
      }
    }
  },
  methods: {
    handleSubmit () {
      console.log('Added')
      this.$emit('add:newEmployee', this.employee)
      this.employee = {
        id: '',
        name: '',
        email: ''
      }
    },
    async handlePost (emp) {
      try {
        const response = await fetch('https://jsonplaceholder.typicode.com/users', {
          method: 'POST',
          body: JSON.stringify({
            id: emp.id,
            name: emp.name,
            email: emp.email
          }),
          headers: {
            'Content-type': 'application/json; charset=UTF-8'
          }
        })
        const data = await response.json()
        console.log(data)
      } catch (error) {
        console.error(error)
      }
    }
  }
}
</script>

<style scoped>

</style>
