

<template>
  <div class="box">
    <transform></transform>
  </div>
</template>

<script>
import transform from './transform.vue'
export default {
  components: {
    transform
  },
  data(){
    return {}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.box {
  display: flex;
  width: 100%;
  height: 100%;
  justify-content: space-around;
  align-items: center; 

}
</style>
