<template>
    <div class="comment-container">
        <div class="title">评论列表</div>
        <div class="publish-info">
            <label>发布时间</label>
             <my-date></my-date>
        </div>
        <div class="comment-info">
            <label for="content">评论内容</label>
            <input type="text" id="content">
            <label for="state">处理状态</label>
            <input type="text" id="state">
            <label for="level">评论层级</label>
            <el-select v-model="selectValue" placeholder="不限" size="small">
                <el-option label="区域一" value="shanghai"></el-option>
                <el-option label="区域二" value="beijing"></el-option>
            </el-select>
        </div>
        <div class="comment-list">
            <div class="batch-reply">
                <el-button size="small" @click="showRely=true">批量回复</el-button>
                <my-batch-reply :visible.sync="showRely"></my-batch-reply>
                <label>当前仅支持对【一级评论】批量回复</label>
            </div>
            <my-table :tableData="pageComments" @reply="replyContent" @lookUp="lookUpComment"></my-table>
            <my-reply :replyVisible.sync="replyVisible" :position="position"></my-reply>
            <comment-info :commentVisible.sync="commentVisible"></comment-info>
            <div class="pagging">
                <my-paging :total="total" :page-size.sync="pageSize" :currentPage.sync="currentPage"></my-paging>
            </div>
        </div>

    </div>
</template>
<script>
    import mydate from '../mydate'
    import mytable from '../table'
    import mypaging from '../paging'
    import batchRely from '../batch-reply'
    import reply from '../reply'
    import commentInfo from '../commentInfo'
    export default {
      data(){
        return {
          selectValue:'',
          comments:[],
          pageSize:20,
          currentPage:1,
          pageComments:[],
          showRely:false,
          replyVisible:false,
          position:{},
          commentVisible:false
        }
      },
      components: {
      'my-date': mydate,
        'my-table':mytable,
        'my-paging':mypaging,
        'my-batch-reply':batchRely,
        'my-reply':reply,
        'comment-info':commentInfo
      },
      created(){
        this.getComments()
      },
      methods:{
        getComments(){
         this.$http.get('http://192.168.0.101:8080/api/getComments')
           .then(res=>{
             return res.json()
           })
           .then(res=>{
             this.comments=res.data
             this.getCurrentComments()
           })
        },
        getCurrentComments(){
          var start=this.currentPage==1?0:(this.currentPage-1)*this.pageSize
          var end=this.currentPage*this.pageSize
          if(end<this.comments.length){
            this.pageComments=this.comments.slice(start,end)
          }else {
            this.pageComments=this.comments.slice(start)
          }
        },
        replyContent(target){
          this.position.x=target.getBoundingClientRect().x
          this.position.y=target.getBoundingClientRect().y
          this.replyVisible=true
        },
        lookUpComment(){
          this.commentVisible=true
        }
      },
      computed:{
        total:function(){
          return this.comments.length
        },
      },
      watch:{
        pageSize:function(){
          this.getCurrentComments()
        },
        currentPage:function(){
          this.getCurrentComments()
        },
        replyVisible:function(){
          console.log(this.replyVisible)
        }
      }
    }
</script>
<style lang="less" scoped>
    .comment-container {
        .title {
            font-size: 16px;
        }
        .publish-info {
            margin: 20px 0;
           label {
               font-size: 14px;
               margin-right: 10px;
           }
        }
        .comment-info {
            margin-bottom: 20px;
            label {
                font-size: 14px;
                margin-right: 10px;
            }
            input {
                height: 30px;
                width: 193px;
                margin-right: 10px;
                border-radius: 4px;
                border:none;
            }

        }
        .comment-list {
            background-color: #fff;
            padding: 20px;
            .batch-reply {
                margin-bottom: 10px;
                label {
                    color:gray;
                    font-size: 12px;
                    margin-left: 5px;
                }
            }
            .pagging {
                display: flex;
                justify-content: flex-end;
                margin-top: 10px;
            }

        }
    }

</style>