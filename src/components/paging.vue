<template>
    <div class="paging-container">
        <div class="left">
            <a @click.prevent="prePage"><i class="el-icon-arrow-left"></i></a>
        </div>
        <div class="pages">
           <div :class="['page',currentPage==item?'currentpage':'']" v-for="(item,index) in pageCount" :key="index">
               <a @click.prevent="changeCurrentPage(item)">{{item}}</a>
           </div>
        </div>
        <div class="right">
            <a  @click.prevent="nextPage">  <i class="el-icon-arrow-right"></i></a>
        </div>
        <select name="sizes" id="sizes" v-model="pageSize" @change="changeSelect">
            <option :value="item" v-for="(item,index) in pageSizes" :key="index">{{item}}条/页</option>
        </select>
    </div>
</template>
<script>
    export default {
      props:{
        'page-size':{
          type:Number,
          default:10
        },
        total:Number,
        pagerCount:{
          type:Number,
          default:7
        },
        currentPage:{
          type:Number,
          default:1
        },
        'page-sizes':{
          type:Array,
          default:function(){
            return [10,20,30,40,50,100]
          }
        }
      },
      computed:{
        pageCount:function(){
          if(this.total==0){
            return 1
          }
          return Math.ceil(this.total/this.pageSize)
        }
      },
      methods:{
        changeSelect(){
          this.$emit("update:pageSize",this.pageSize)
        },
        prePage(){
          if(this.currentPage==1) {
            return
          }
          this.$emit('update:currentPage',this.currentPage-1)
        },
        nextPage(){
          if(this.currentPage==this.pageCount){
            return
          }
          this.$emit('update:currentPage',this.currentPage+1)
        },
        changeCurrentPage(page){
          this.$emit('update:currentPage',page)
        }
      }
    }
</script>
<style lang="less" scoped>
    .paging-container {
        display: flex;
        justify-content: flex-start;
        .left,
        .right,
        .page  {
            width: 25px;
            height: 25px;
            text-align: center;
            vertical-align: center;
            border-radius: 5px;
            margin-right: 10px;
        }
        .left,.right{
            border:1px solid lightgray;
        }
        .pages{
            display: flex;
            justify-content: flex-start;
        }
        .page {
            border:1px solid lightgray;
        }
        .currentpage {
            border:1px solid dodgerblue;
        }

    }
</style>