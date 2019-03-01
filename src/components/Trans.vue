<template>
   <div class="trans">
      {{msgs}}
    </div>
</template>

<script>
import bus from '../bus.js'
export default {
    name:'Trans',
    mounted(){
     bus.$on('get-values',(data)=>{
            this.msgs = data
     })
     bus.$on('clear-val',(msg) =>{
         this.msgs=msg;
     })
    },
    data(){
        return {
          msgs:''
        }
    }
}
</script>
<style scoped  lang="">
  .trans{
      width: 500px;
      height: 300px;
      background: #CCC;
      margin-top: 15px;
  }
</style>