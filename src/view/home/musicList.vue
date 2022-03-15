<template>
    <div class="newList">
        <div class="nav">
            <a href="#">榜单</a>
            
            <div class="more">
                <a>更多</a>
            </div>
        </div>
        <div class="songs">
            <el-table :data="tableData" stripe style="width: 100%">
                <!-- 利用空表来留出前端间距 -->
                <el-table-column width="60"/>
                <el-table-column prop="id" label="" width="180"/>
                <el-table-column width="100"/>
                <el-table-column prop="author" label="" width="180"/>
                <el-table-column prop="song" label=""/>
                <el-table-column width="150" label="" fixed="right">
                    <!-- 这里是利用插槽的方式进行传值操作index是序号，row是所有一行内的数据 -->
                    <template v-slot="scope">
                        <el-button size="mini" @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
                        <el-button size="mini" type="danger" @click="handleDelete(scope.$index, scope.row)">删除</el-button>
                    </template>
                </el-table-column>
            </el-table>
        </div>
    </div>
</template>
<script>
    export default {
        props: {
            tableData: {
                type: Array,
                required: true
            }
        },
        methods: {
            // 编辑操作
            handleEdit(index, row) {
                console.log(index);
                console.log(row.song);
            },
            // 删除操作
            handleDelete(index, row) {
                console.log(index);
                console.log(row);
            }
        }
    }
</script>
<style lang="less" scoped>
    @import './common.less';
    .newList {
        margin-bottom: 50px;
        .songs {
            margin-top: 25px;
        }
    }
</style>