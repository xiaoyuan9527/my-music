<template>
    <div v-if="token" class="login">
        <span><a href="#">用户中心</a></span>
        <span><a @click="outEvt">退出登陆</a></span>
    </div>
    <div v-else class="login">
        <span><a @click="dialogFormVisible = true">登陆</a></span>

        <el-dialog title="登陆" center="center" :visible.sync="dialogFormVisible">
            <el-form :model="form">
                <el-form-item label="账号" :label-width="formLabelWidth">
                <el-input v-model="form.name" :label-width="formLabelWidth" autocomplete="off"/>
                </el-form-item>
                <el-form-item label="密码" :label-width="formLabelWidth">
                <el-input v-model="form.name" :label-width="formLabelWidth" autocomplete="off"/>
                </el-form-item>
                
                
            </el-form>
            <div slot="footer" class="dialog-footer">
                <el-button @click="dialogFormVisible = false">取 消</el-button>
                <el-button type="primary" @click="loginEvt">确 定</el-button>
            </div>
        </el-dialog>
    </div>
</template>
<script>
    export default {
        props: {
            token: {
                type: String,
                required: false
            }
        },
        data() {
            return {
                dialogFormVisible: false,
                form: {
                    name: '',
                    region: '',
                    delivery: false,
                    type: [],
                    resource: '',
                    desc: ''
                },
                formLabelWidth: '80px'
            }
        },
        methods: {
            // 模拟储存token数据
            loginEvt() {
                this.dialogFormVisible = false
                let info = 'xxx'
                this.$store.commit('common/mutationToken', info)
                location.reload()
            },
            outEvt() {
                let info = ''
                this.$store.commit('common/mutationToken', info)
                location.reload()
            }
        }
    }
</script>
<style lang="less" scoped>
    .login {
        position: absolute;
        right: 0;
        top: 25px;
        span {
            padding-left: 10px;
            a {
                cursor: pointer;
                font-size: 14px;
                list-style: none;
                text-decoration: none;
                color: #787878;
            }
        }
    }
</style>