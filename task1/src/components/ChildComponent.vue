<template>
    <table>
    <thead>
      <tr>
        <th>Student Name</th>
        <th>Student Class</th>
        <th>Student Section</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(item, index) in data" :key="index">
      <td>{{ item.studentName }}</td>
      <td>{{ item.studentClass }}</td>
      <td>{{ item.studentSection }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default{
    props:{
        data:{
            type: Array
        }
    }
}
</script>

<style>

</style>