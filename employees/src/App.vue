<template>
  <div id="app" class="small-container">
    <h1>Employees</h1>
    <employee-form v-on:add:newEmployee="handleIncoming"/>
    <br>
    <br>
    <employee-table
    v-bind:employees="employees"
    v-on:delete:employee="handleDelete"
    v-on:edit:employee="handleEdit"
    />
  </div>
</template>

<script>
import EmployeeTable from './components/EmployeeTable'
import EmployeeForm from './components/EmployeeForm'

export default {
  name: 'App',
  components: {
    EmployeeTable,
    EmployeeForm
  },
  data () {
    return {
      employees: []
    }
  },
  methods: {
    handleIncoming (newEmployee) {
      console.log('Added new employee!')
      this.employees = [...this.employees, newEmployee]
    },
    handleDelete (emp) {
      console.log('Deleting ID: ' + emp)
      this.employees = this.employees.filter((emps) => {
        return emps.id !== emp
      })
    },
    handleEdit (id, empUpdate) {
      this.employees = this.employees.map(employee =>
        employee.id === id ? empUpdate : employee
      )
    },
    async getEmployees () {
      try {
        const response = await fetch('https://jsonplaceholder.typicode.com/users')
        const data = await response.json()
        this.employees = data
      } catch (error) {
        console.error(error)
      }
    }
  },
  mounted () {
    this.getEmployees()
  }
}

</script>

<style>
button {
    background: #009435;
    border: 1px solid #009435;
  }

.small-container {
    max-width: 680px;
  }
</style>
