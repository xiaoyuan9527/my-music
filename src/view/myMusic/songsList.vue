<template>
    <div class="musicList">
        <el-collapse v-model="activeName" accordion>
            <el-collapse-item title="ㅤㅤ创建的歌单" name="1">
                <ul v-for="(item, index) in songsList" :key="index">
                    <li @click="chickOne">
                        <div>
                            <img width="40" :src="item.url" alt="" class="image">
                        </div>
                        <div class="infoName">
                            <p>{{item.name}}</p>
                            <span>{{item.songs}}首</span>
                        </div>
                    </li>
                </ul>
            </el-collapse-item>
        </el-collapse>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                activeName: '1',
                number: ''
            }
        },
        props: {
            songsList: {
                type: Array,
                required: true
            }
        },
        methods: {
            chickOne() {
                this.$emit('getOne', this.number)
            }   
        }
    }
</script>
<style lang="less" scoped>
    .musicList {
        // height: calc(100% - 48px - 24px);
        background: #fff;
        width: 240px;
        min-height: 1000px;
        .el-collapse-item {
            
            li {
                padding: 10px 24px 3px;
                &:hover {
                    background: #f5f5f5;
                }
                display: flex;
                .infoName {
                    padding-left: 14px;
                    span {
                        color: #999;
                    }
                }
            }
        }
    }
</style>