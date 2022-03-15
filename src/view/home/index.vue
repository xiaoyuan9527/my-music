<template>
    <PageLayout :buttonState=buttonState :token="token">
        <!-- 组件化 -->
        <banner :bannerUrl="bannerUrl" />
        <div class="recommend">
            <hot-disc :tabList="tabList" :MusicTab="MusicTab" />
            <new-disc :newMusicTab="newMusicTab" />
            <music-list :tableData="tableData" />
        </div>
        <footer>
            <div class="content">
                <span>本网页由个人开发，请勿传播，以免法律责任</span>
            </div>
        </footer>
    </PageLayout>
</template>
<script>
    // 引入组件
    import Banner from './banner.vue'
    import HotDisc from './hotDisc.vue'
    import NewDisc from './newDisc.vue'
    import MusicList from './musicList.vue'
    export default {
        components: {
            Banner,
            HotDisc,
            NewDisc,
            MusicList
        },
        data() {
            return {
                // info是子组件传回来的，必须先定义
                state: false,
                name: '小花',
                age: '18',  
                token: '',
                buttonState: 'foundMusic',
                bannerUrl: [
                    // 引用网络地址
                    { id: 1, url: 'http://p1.music.126.net/7afzcxfhYu9bMw-M0dvt7A==/109951166652444979.jpg?imageView&quality=89' },
                    { id: 2, url: 'http://p1.music.126.net/bOlmUZ15DSRocTgISF-z7g==/109951166652450941.jpg?imageView&quality=89' },
                    { id: 3, url: 'http://p1.music.126.net/fAtJBUEMP0P9kKmNQcyFLA==/109951166650559696.jpg?imageView&quality=89' }
                ],
                tabList: [
                    { url: '#', name: '华语', iden: '|' },
                    { url: '#', name: '流行', iden: '|' },
                    { url: '#', name: '摇滚', iden: '|' },
                    { url: '#', name: '电子', iden: '|' },
                    { url: '#', name: '日韩' }
                ],
                MusicTab: [
                    { url: 'http://p1.music.126.net/QfSEhlLBfFZaqzIum2k3yQ==/109951165603084096.jpg?param=140y140', text: '猪猪的自我修养' },
                    { url: 'http://p1.music.126.net/GQkPC35zjYvJj5Q_KWs21Q==/109951165685006345.jpg?param=140y140', text: '颤抖吧，凡人' },
                    { url: 'http://p1.music.126.net/smz83u5KdKPaDYggOaJV9Q==/109951166526033909.jpg?param=140y140', text: '二刺猿哭吧，哭吧' },
                    { url: 'http://p1.music.126.net/O2Y9QxIwRCM7amY0wMN7mw==/109951166596392065.jpg?param=140y140', text: '机车时刻' },
                    // 方便，直接拷贝的
                    { url: 'http://p1.music.126.net/GQkPC35zjYvJj5Q_KWs21Q==/109951165685006345.jpg?param=140y140', text: '颤抖吧，凡人' },
                    { url: 'http://p1.music.126.net/O2Y9QxIwRCM7amY0wMN7mw==/109951166596392065.jpg?param=140y140', text: '机车时刻' },
                    { url: 'http://p1.music.126.net/QfSEhlLBfFZaqzIum2k3yQ==/109951165603084096.jpg?param=140y140', text: '猪猪的自我修养' },
                    { url: 'http://p1.music.126.net/smz83u5KdKPaDYggOaJV9Q==/109951166526033909.jpg?param=140y140', text: '二刺猿哭吧，哭吧' }
                ],
                newMusicTab: [
                    { url: 'http://p1.music.126.net/E6yrCYRc5rs4FmdchSdSwg==/109951166655027184.jpg?imageView&quality=89', text: '猪猪的自我修养' },
                    { url: 'http://p1.music.126.net/5KZXjFBc2CGYtrJ6GDiRIw==/109951166653877485.jpg?imageView&quality=89', text: '颤抖吧，凡人' },
                    { url: 'http://p1.music.126.net/O9WS9vt3X2AD_rKWStTFHQ==/109951166654720337.jpg?imageView&quality=89', text: '二刺猿哭吧，哭吧' },
                    { url: 'http://p1.music.126.net/5Q4WdJf2T59F6onhKsjOig==/109951166654988627.jpg?imageView&quality=89', text: '机车时刻' }
                ],
                tableData: ''
            }
        },
        created() {
            this.getToken()
            this.tableData = Array(3).fill('').map( (_, i) => {
                    return { id: i + 1, author: Math.random() > .5? '男': '女', song: '1731399990' + i }
                })
        },
        methods: {
            getToken() {
                let info = this.$store.getters['common/token']
                if (info) {
                    this.token = info
                }
            }
        }
    }
</script>
<style lang="less" scoped>
    .recommend {
        background: #fff;
        border-left: 1px solid #C10D0C;
        border-right: 1px solid #C10D0C;
        box-sizing: border-box;
        width: 1000px;
        margin: 0 auto;
        padding: 40px 20px 20px;
    }
    footer {
        background: #eee;
        border-top: 1px solid #099;
        height: 180px;
        .content {
            width: 1000px;
            margin: 0 auto;
            text-align: center;
            line-height: 180px;
            color: #999;
        }
    }
</style>