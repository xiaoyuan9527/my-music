<template>
    <div class="newDisc">
        <div class="nav">
            <a href="#">新碟上映</a>
            
            <div class="more">
                <a>更多</a>
            </div>
        </div>
        <div class="banner">
            <el-carousel :interval="4000" type="card" height="200px">
                <el-carousel-item v-for="(item, index) in newMusicTab" :key="index">
                    <img :src="item.url" alt="" class="image">
                </el-carousel-item>
            </el-carousel>
        </div>
    </div>
</template>
<script>
    export default {
        props: {
            newMusicTab: {
                type: Array,
                required: true
            }
        }
    }
</script>
<style lang="less" scoped>
    @import './common.less';
    .banner {
        margin-top: 50px;
        margin-bottom: 30px;
        img {
            width: 100%;
        }
    }
</style>