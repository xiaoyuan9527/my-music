<template>
    
    <div class="hot">
        <!-- 上边按钮 -->
        <div class="nav">
            <a href="#">热门推荐</a>
            <div v-for="(item, index) in tabList" :key="index" class="tab">
                <a :href="item.url">{{item.name}}</a>
                <span>{{item.iden}}</span>
            </div>
            <div class="more">
                <a>更多</a>
            </div>
        </div>
        <!-- 下边选择播放音乐 -->
        <div class="chooseMusic">
            <div v-for="(item, index) in MusicTab" :key="index" class="box">
                <i><img width="180" :src="item.url" alt=""></i>
                <span>{{item.text}}</span>
            </div>
        </div>
    </div>
</template>
<script>
    export default {
        props: {
            tabList: {
                type: Array,
                required: true
            },
            MusicTab: {
                type: Array,
                required: true
            }
        }
    }
</script>
<style lang="less" scoped>
    @import './common.less';
    .chooseMusic {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
        padding-top: 45px;
        .box {
            width: 200px;
            height: 200px;
            margin-bottom: 50px;
            i {
                display: block;
                text-align: center;
                margin-bottom: 10px;
            }
            span {
                cursor: pointer;
                padding-left: 10px;
            }
        }
    }
</style>