<template>
   <div class="box">
      <Pro/>
   </div>
</template>

<script>
import Pro from './pro'
export default {
  name: 'HelloWorld',
  components:{
   Pro
  },
  data () {
     return {

        }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.box{
  width:500px;
  height:100px;
  border:2px solid #000;
}
</style>

