<template>
  <div id="app">
    <student :a=1></student>
  </div>
</template>

<script>
import Student from './components/Student.vue'
import mixin from './mixin'

export default {
  name: 'App',
  data() {
    return {
      aa : 222
    }
  },
  components: {
    Student
  },
  mixins:[mixin]
}
</script>

<style>
</style>
