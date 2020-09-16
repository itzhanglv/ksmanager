<template>
    <div class="batch-reply-container" v-show="visible">
        <div class="mask" @click="$emit('update:visible',false)"></div>
        <div class="content">
        <div class="title">
            <span>批量回复</span>
            <i class="el-icon-close" @click="$emit('update:visible',false)"></i>
        </div>
        <div class="reply-content">
            <div class="info">
                <span>
                    <i class="el-icon-warning-outline"></i>
                    当前仅支持对【一级评论】批量回复，二级评论已自动过滤
                </span>
                <div>
                <span>已选一级评论(0)</span>
                <a>展开</a>
                </div>
            </div>
            <div class="comments">
                <my-table></my-table>
            </div>
            <hr>
            <div class="comment-content">
                <textarea name="" id="" cols="30" rows="10" placeholder="请输入回复内容，回复内容将经过审核"></textarea>
                <span class="letters">0/255</span>
            </div>
        </div>
        <div class="footer">
            <el-button size="mini" @click="$emit('update:visible',false)">取消</el-button>
            <el-button size="mini">发布</el-button>
        </div>
        </div>
    </div>
</template>
<script>
    import commentTable from './comment-table'
    export default {
      props:[
        'visible'
      ],
      components:{
        'my-table':commentTable
      }
    }
</script>
<style lang="less" scoped>
.batch-reply-container {
    .mask {
        width: 100vw;
        height: 100vh;
        background-color: rgba(0,0,0,0.3);
        position: absolute;
        top: 0;
        left: 0;
        z-index: 99;
    }
    .content {
        width:600px;
        height: 380px;
        display: flex;
        flex-direction: column;
        background-color: #fff;
        position: absolute;
        top: 200px;
        left: 50%;
        transform:translateX(-50%);
        z-index: 100;
        padding: 20px;
        .title {
            display: flex;
            justify-content: space-between;
            border-bottom: 2px solid lightgray;
            vertical-align: center;
            padding-bottom:10px;
        }
        .reply-content {
            margin-top: 5px;
            .info {
                display: flex;
                justify-content: space-between;
                font-size: 12px;
                color: gray;
                a {
                    margin-left: 10px;
                    color: dodgerblue;
                }
            }
            .comments {
                width: 100%;
            }
            .comment-content {
                margin-top: 10px;
                position: relative;
                textarea {
                    width: 100%;
                    /*border:none;*/
                    border:1px solid lightgray;
                    border-radius: 5px;
                    padding: 5px;
                    box-sizing: border-box;
                    /*color: lightgray;*/
                    outline: none;
                }
                .letters {
                    position: absolute;
                    bottom: 5px;
                    right: 6px;
                    font-size: 10px;
                    color: lightgray;
                }
            }
        }
        .footer {
            width: 100%;
            height: 50px;
            border-top: 1px solid lightgray;
            position:absolute;
            left: 0;
            bottom: 0;
            display: flex;
            justify-content: flex-end;
            padding: 10px;
            box-sizing: border-box;
        }
    }

}
</style>