// 这儿定义全局样式
// 意义在于全局注册被当做都被使用，换句话说这个组件也是子组件
// 即需要porps 同时需要slot 
<template>
    <div class="main">
        <header :style="how === 'new'? 'padding-right: 17px' : 'padding-right: 0px'">
            <div class="content">
                <div class="logo">
                    <h1>派蒙音乐</h1>
                </div>
                <ul>
                    <!-- 子->父传值，通过传入的值进行判断 -->
                    <!-- 通过属性的选择，三目方法进行校验是现在处于那个页面 -->
                    <li @click="$router.push('/home')" :class="buttonState === 'foundMusic'? 'changeBackground' : 'defaultBackground'">发现音乐</li>
                    <li :plain="true" @click="gotoFn" :class="buttonState === 'myMusic'? 'changeBackground' : 'defaultBackground'">我的音乐</li>
                    <li @click="goOther" :class="buttonState === 'Musician'? 'changeBackground' : 'defaultBackground'">音乐人</li>
                </ul>
                <div class="search">
                    <input type="text" name="" id="">
                </div>
                <login :token="token" />
            </div>
            <!-- 待完善，功能模块 -->
            <div v-if="buttonState === 'foundMusic'" class="footer">
                <ul>
                    <li v-for="it in lists" :key="it.id">{{it.name}}</li>
                </ul>
            </div>
            <div v-else class="footerLess">

            </div>
        </header>
        <!-- 这是除开头部的部分，利用slot引入 -->
        <article>
            <slot/>
        </article>
        
    </div>
</template>
<script>
    import Login from './login.vue'
    export default {
        components: {
            Login
        },
        data() {
            return {
                lists: [
                { id: 1, name: '小花' },
                { id: 2, name: '小红' },
                { id: 3, name: '小莉' }
                ]
            }
        },
        props: {
            how: {
                type: String
            },
            buttonState: {
                type: String,
                required: true,
                // 默认为发现音乐界面
                default: 'foundMusic'
            },
            token: {
                type: String,
                required: false
            },
            // 这里是接受下红边的数据的
            list: {
                type: Array,
                // 这里是测试写的fasle
                required: false,
                default: () => []
            }
        },
        methods: {
            gotoFn() {
                let result = this.$store.getters['common/token']
                if (result) {
                    this.$router.push('/myMusic')
                } else {
                    this.$message.error('请先登陆')
                }
            },
            goOther() {
                let url = 'https://music.163.com/st/musician'
                // 在新页面跳转
                window.open(url,"_blank")
                // 当前页面跳转
                // window.location = url
            }
        }
    }
</script>
// less的样式
<style lang="less" scoped>
    @import './PageLayout.less';
</style>