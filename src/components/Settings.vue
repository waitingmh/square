<template>
     <div class="two">
           <select name="" id="" v-model="type">
               <option>自动检测语言</option>
               <option value="English">English</option>
               <option value="Chinese">Chinese</option>
           </select>
           <button @click="translator">翻译</button>
           <button @click="clear">清空</button>
       </div>
</template>

<script>
import bus from '../bus.js'
import data from '../common/mock'
import data1 from '../common/mock1'
export default {
    name:'Setting',
    methods:{
      translator(){
         if(this.type === 'English'){
            !this.msg ? alert('您还未输入任何翻译的文本') : bus.$emit('get-values', this.data[this.msg]);
         }else{
            !this.msg ? alert('您还未输入任何翻译的文本') : bus.$emit('get-values', this.data1[this.msg]);
         }
      },
      clear(){
          bus.$emit('clear-val',this.val)
      }
    },
    mounted(){
        bus.$on('get-value',(val)=>{
            this.msg=val
         })
    },
    data(){
        return {
          msg:'',
          val:'',
          data:data,
          data1:data1,
          type: 'English',
        }
    }
}
</script>
<style scoped  lang="scss">
.two{
         width: 100%;
         display: flex;
         select{
         width: 120px;
         height: 30px;
         margin-right: 250px;
         }
         button{
             width:120px;
             height: 30px;
             margin-right: 10px;
         }
     }
</style>