<template>
    <div class="comment-content">
        <textarea name="" id="" cols="30" rows="10" placeholder="请输入回复内容，回复内容将经过审核"></textarea>
        <span class="letters">0/255</span>
    </div>
</template>
<script></script>
<style lang="less" scoped>
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
</style>