<template>
  <table>
    <tr>
      <th>Name</th>
      <th>Kurs</th>
      <th>Age</th>
      <th>Gpa</th>
    </tr>
    <tr v-for="student in students" :key="student">
      <th>{{student.name}}</th>
      <th>{{student.kurs}}</th>
      <th>{{student.vazrast}}</th>
      <th>{{student.gpa}}</th>
    </tr>
  </table>
  <router-link to="/student/edit" class="addLink">+ Добавить Студента</router-link >
</template>

<script>
export default {
  data() {
    return {
      students: ""
    }
  },
  methods:{
  }
  ,
  mounted() {
    fetch("http://127.0.0.1:8000/students")
      .then(res => res.json())
      .then(data => this.students = data)
  }
}
</script>

<style scoped>
table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

td, th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}
.addLink{
  font-size: 19px;
  position: relative;
  top: 10px;
  left: 1000px;
  border: #2c3e50;
  color: #2c3e50;
  border-bottom:1.5px solid #2c3e50 ;
}
.addLink:hover{
  color: #dddddd;
}
</style>
