<template>
    <div>
        <h4>this is Child</h4>
        <button @click="send">点击子传父</button>
        <span>{{fatherValue}}</span>
    </div>
</template>
<script>
    export default {
        // 当设置props以后，接收到的数据不用data，直接用props就好
        props: {
            fatherValue: {
                // 被传递的值类型
                type: String,
                // 是否必传
                required: true,
                // 默认值
                default: ''
            }
        },
        data() {
            return {
                childValue: ''
            }
        },
        methods: {
            send() {
                this.childValue = '这是子值'
                // 这里是将值传递给父代
                // 调用父代自定义的操作，然后传值
                this.$emit('getValue', this.childValue)
            }
        }
    }
</script>