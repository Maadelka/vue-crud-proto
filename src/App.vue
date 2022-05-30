<template>
  <!-- <comp1 :sapa="sapa" /> -->
  <arr/>

</template>







<script>
  import comp1 from './components/comp1.vue'
  import arr from './components/arr.vue'
  export default {
    components:{
      comp1,
      arr
    },
    data(){
      return{
        sapa: 'hello andhika!'
      }
    }
  }
</script>
