<template>
   <div class="wrap">
     <div class="square">
       <span v-for="(i,v) in arrs" :key="v" @click="getIndex(v,i)" :class="{'space':!i}">{{i}}</span>
     </div>
     <button @click="reset">重置游戏</button>
   </div>
</template>
<script>
export default {
  name: 'Square',
  mounted(){
     let arr=[]
     for(let i = 1;i < 16;i++){
         arr.push(i)
     }
     arr = arr.sort(() => {
       return  Math.random() - 0.5
     })
     this.arrs = arr;
     this.arrs.push('')
  },
  methods:{
   getIndex(ind,v){
      if(ind === this.default - 1 || ind === this.default + 1 || ind === this.default - 4 || ind === this.default + 4){
         this.arrs[this.default] = this.arrs[ind]
         this.$set(this.arrs,ind,'')
         this.default = ind ;
      }
   },
   reset(){
     let arr=[]
     for(let i = 1;i < 16;i++){
         arr.push(i)
     }
     arr = arr.sort(() => {
       return  Math.random() - 0.5
     })
     this.arrs = arr;
     this.arrs.push('')
   }
  },
  data () {
    return {
      arrs:[],
      cur:'',
      default:15
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.wrap{
  width: 480px;
  height: 480px;
  border:1px solid #CCC;
  box-shadow: 3px 3px 5px #CCC,-3px -3px 5px #CCC;
  background: #FFF;
  margin: 20px auto;
  padding-top: 20px;
  box-sizing: border-box;
  .square{
    width: 380px;
    height: 380px;
    background: #CCC;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    span{
       width: 24.4%;
       height: 93px;
       background: orange;
       border:1px solid #CCC;
       text-align: center;
       line-height: 93px;
       font-weight: 600;
    }
    .space{
      background: #CCC;
    }
  }
  button{
    width: 380px;
    height: 30px;
    background: orange;
    margin-top: 20px;
    outline: 0;
    border-radius: 5px;
    border: 1px solid orangered;
    color: #FFF;
  }
}
</style>
