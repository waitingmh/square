<template>
    <div class="translate">
       <textarea 
       v-model="curCon"
       @blur="getValue()"
       ></textarea>
       <setting />
       <Trans />
    </div>
</template>

<script>
import bus from '../bus.js'
import Setting from './Settings'
import Trans from './Trans'
export default {
    name:'Translate',
    components:{
        Setting,
        Trans
    },
    methods:{
        getValue(){
           bus.$emit('get-value',this.curCon)
        }
    },
    mounted(){
        bus.$on('clear-val',(msg) =>{
        this.curCon=msg;
     })
    },
    data(){
        return {
          curCon:'',
        }
    }
}
</script>
<style scoped  lang="scss">
 .translate{
     width: 500px;
     height: 500px;
     display: flex;
     flex-direction: column;
     textarea{
         width: 500px;
         height:200px;
         border: 0;
         border-bottom: 1px solid #CCC;
         margin-bottom: 20px;
     }
     
     
 }
</style>