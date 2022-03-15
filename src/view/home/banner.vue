<template>
    <div class="banner">
        <el-carousel :interval="5000" arrow="always" height="380px">
            <el-carousel-item v-for="item in bannerUrl" :key="item.id">
                <img :src="item.url" class="image">
            </el-carousel-item>
        </el-carousel>
    </div>
</template>
<script>
    export default {
        props: {
            bannerUrl: {
                type: Array,
                required: true
            }
        }
    }
</script>
<style lang="less" scoped>
    .banner {
        width: 1000px;
        margin: 0 auto;
        img {
            width: 100%;
            opacity: 0.75;
            // line-height: 300px;
            margin: 0;
        }
    }
</style>