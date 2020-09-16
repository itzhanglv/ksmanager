<template>
    <transition>
      <div class="container" v-show="commentVisible">
        <div class="mask" @click="$emit('update:commentVisible',false)"></div>
        <div class="commentInfo-container" >

        <div class="title">
            <span>评论详情</span>
            <a @click.prevent="$emit('update:commentVisible',false)"> <i class="el-icon-close"></i></a>
        </div>
        <div class="content">
            <div class="currentComment">
                <p class="comment">这东西好吃吗</p>
                <p class="user-info">
                    <span>测试用户</span>
                    <span>08/06 00:00</span>
                    <span>88</span>
                </p>
            </div>
            <div class="comment-reply">
                 <p class="total-reply">88条回复</p>
                <ul class="reply-list">
                    <li v-for="(item,index) in 5" :key="index">
                        <p>这东西好吃吗</p>
                        <p>
                            <span>测试用户</span>
                            <span>08/06 00:00</span>
                            <span>88</span>
                        </p>
                    </li>
                </ul>
            </div>
        </div>
    </div>
      </div>
    </transition>
</template>
<script>
    export default {
      props:['commentVisible'],
      methods:{
      }
    }
</script>
<style lang="less" scoped>
    .v-enter,
    .v-leave-to {
        opacity: 0;
        transform:translateX(500px);
    }
    .v-enter-active,
    .v-leave-active {
        position:absolute;
        top: 0;
        right: 0;
        transition:all 0.5s ease;
    }
    .v-move {
        opacity: 1;
        transition:transform 1s
    }
    .container {
    .mask {
        width: 100vw;
        height: 100vh;
        background-color: rgba(0,0,0,0.3);
        position:absolute;
        top: 0;
        left: 0;
        z-index: 100;
    }
    .commentInfo-container {
        width: 500px;
        height: 100vh;
        background-color: #fff;
        position: absolute;
        right: 0;
        top: 0;
        z-index: 200;
        .title {
            height: 40px;
            display: flex;
            justify-content: space-between;
            font-size: 14px;
            border-bottom: 1px solid lightgrey;
            align-items: center;
            padding: 0 10px;
        }
        .content {
            padding:10px;
            .currentComment {
                display: flex;
                flex-direction: column;
                justify-content: space-between;
                .comment {
                    font-weight: 700;
                    font-size: 12px;
                    margin-bottom: 5px;
                }
                .user-info {
                    color: darkgrey;
                    font-size: 10px;
                    span {
                        margin-right: 10px;
                    }
                }
            }
            .comment-reply {
                margin-top: 15px;
                .total-reply {
                    font-size: 12px;
                    margin-bottom: 10px;
                }
                .reply-list {
                    width: 100%;
                    list-style: none;
                    li {
                        display: flex;
                        flex-direction: column;
                        justify-content: space-between;
                        background-color: rgba(0,0,0,0.01);
                        margin-bottom: 5px;
                        font-size: 12px;
                        padding: 5px 10px;
                        p {
                            margin-bottom: 5px;
                            span {
                                color: darkgrey;
                                margin-right: 10px;
                            }
                        }
                    }
                }
            }
        }
    }
    }
</style>