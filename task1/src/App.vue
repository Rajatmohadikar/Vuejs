<template>
  <div>
    <child-component :data="myArr"></child-component>
  </div>
  
</template>

<script>
import ChildComponent from './components/ChildComponent.vue'

export default{
  name: 'App',
  components: {
    ChildComponent
  },
  data(){
    return {
      myArr: [
        {
          studentName: "Jack",
          studentClass: 6,
          studentSection: "a"
        },
        {
          studentName: "Tom",
          studentClass: 6,
          studentSection: "a"
        }
      ]
    };
  }
};

</script>

<style>

</style>
