<template>
    <div class="reply-container" v-show="replyVisible" ref="reply">
        <div class="dialog1"></div>
        <div class="dialog2"></div>
        <div class="title">回复</div>
        <div class="content">
           <my-textarea></my-textarea>
        </div>
        <div class="sure">
            <el-button type="text" size="small" @click="$emit('update:replyVisible',false)">取消</el-button>
            <el-button size="small">发布</el-button>
        </div>
    </div>
</template>
<script>
    import myTextarea from './mytextarea'
    export default {
      data(){
        return {
        }
      },
      updated(){
        this.setPosition()
      },
      methods:{
        setPosition(){
          if(this.replyVisible){
            this.$refs.reply.style=`position:absolute;
        top:${this.position.y+50}px;
        left:${this.position.x-477}px;`
          }
        }
      },
      components:{
        'my-textarea':myTextarea
      },
      props:['replyVisible','position'],
      watch:{
        replyVisible:function(){
          // console.log(this.replyVisible)
        }
      }

    }
</script>
<style lang="less" scoped>
    .reply-container {
       width:500px;
        height: 250px;
        background-color: #fff;
        z-index: 999;
        box-shadow: -2px 0px 3px 1px lightgrey,0px -2px 3px 1px lightgrey,2px 0px 3px 1px lightgrey,0px 2px 3px 1px lightgrey;
        padding: 10px;
        .sure {
            display: flex;
            justify-content: flex-end;
            margin-top: 10px;
        }
        .dialog1 {
            position: absolute;
            top:-16px;
            left: 480px;
            width:0;
            height:0;
            font-size:0;
            border:solid 8px;
            border-color:transparent transparent #fff transparent;
            z-index: 100;
        }
        .dialog2 {
            position: absolute;
            top:-16px;
            left: 480px;
            width:0;
            height:0;
            font-size:0;
            border:solid 8px;
            border-color:transparent transparent gray transparent;
        }
    }
</style>