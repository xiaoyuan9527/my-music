<template>
    <div class="box">
        <PageLayout :buttonState=buttonState :token="token" :how="how">
            <div class="content">
                <songs-list @getOne="getOnes" :songsList="songsList" />
                <div class="music">
                    <el-table :data="tableData" style="width: 100%" height="100%">
                        <el-table-column fixed prop="" label="" width="80"/>
                        <el-table-column fixed prop="id" label="编号" width="120"/>
                        <el-table-column prop="name" label="名字" width="200"/>
                        <el-table-column prop="hot" label="热度" width="160"/>
                        <el-table-column fixed="right" width="120" label="操作">
                            <template v-slot="scope">
                                <el-button @click="handleClick(scope.row)" type="text" size="small">编辑</el-button>
                                <el-button @click="deleteRow(scope.row)" type="text" size="small">删除</el-button>
                            </template>
                        </el-table-column>
                    </el-table>
                    <div class="under">

                    </div>
                </div>
            </div>
        </PageLayout>
    </div>
</template>
<script>
    import SongsList from './songsList.vue'
    export default {
        components: {
            SongsList
        },
        data() {
            return {
                state: "xiaoyuan",
                buttonState: 'myMusic',
                how: 'new',
                token: 'xxx',
                number: '',
                tableData: [],
                songsList: [],
                songList: Array(14).fill('').map( (_, i) => {
                    return { id: i + 1, name: '火红的萨日朗' + i, hot: Math.random() > .5? 'hot' : 'low' }
                })
            }
        },
        created() {
            this.tableData = this.songList
            this.songsList = [
                { url: 'https://p1.music.126.net/pETQnye5ooWtzXSCC0qbeQ==/1744924953286126.jpg?param=40y40', name: '我的歌单1', songs: this.songList.length },
                { url: 'https://p1.music.126.net/pETQnye5ooWtzXSCC0qbeQ==/1744924953286126.jpg?param=40y40', name: '我的歌单2', songs: this.songList.length }
            ]
            console.log(this.songsList);
        },
        methods:{
            handleClick() {

            },
            deleteRow() {
                
            },
            getOnes(data) {
                this.number = data
                console.log(data);
            }
        }
    }
</script>
<style lang="less" scoped>
    
    .box {
        background: #e5e5e5;
        display: block;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        .content {
            display: flex;
            margin: 0 auto; // 使父容器水平居中显示
            width: 1000px;
            .music {
                flex: 1;
                bottom: 0;
                overflow-y: auto;
                margin: 0 0 0 20px;
                width: 760px;
                height: 100%;
                max-height: 660px;
            }
            .under {
                width: 100%;
                height: 320px;
                background: #fff;
            }
        }
    }
    
</style>