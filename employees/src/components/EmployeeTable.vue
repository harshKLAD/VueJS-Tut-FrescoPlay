<template>
    <div id="employee-table">
    <table>
      <thead>
        <tr>
          <th>Employee ID</th>
          <th>Employee name</th>
          <th>Employee email</th>
          <th></th>
        </tr>
      </thead>
      <tbody v-bind:key="emp.id" v-for="emp in employees">
        <tr>
          <td>{{ emp.id }}</td>

          <td v-if="editing === emp.id">
            <input type="text" v-model="emp.name" />
          </td>
          <td v-else>{{emp.name}}</td>

          <td v-if="editing === emp.id">
            <input type="text" v-model="emp.email" />
          </td>
          <td v-else>{{emp.email}}</td>

          <td v-if="editing === emp.id">
            <button v-on:click="editingEmployee(emp)">Save</button>
            <button class="muted-button" v-on:click="cancelEdit(emp)">Cancel</button>
          </td>
          <td v-else>
            <button v-on:click="editEmployee(emp)">Edit</button>
            <button v-on:click="$emit('delete:employee', emp.id)">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'employee-table',
  props: {
    employees: Array
  },
  data () {
    return {
      editing: null
    }
  },
  methods: {
    editEmployee (emp) {
      this.$emit('edit:employee', emp.id, emp)
      this.cachedEmployee = Object.assign({}, emp)
      this.editing = emp.id
    },
    editingEmployee (emp) {
      if (emp.name === '' || emp.email === '') {
        console.log('Field empty')
        return
      }
      this.$emit('edit:employee', emp.id, emp)
      this.editing = null
    },
    cancelEdit (emp) {
      Object.assign(emp, this.cachedEmployee)
      this.editing = null
    }
  }
}
</script>

<style scoped>
button {
    padding: 5px
  }
</style>
