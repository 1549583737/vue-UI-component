<template>
    <div id="app">
        <selectComponent :subject="subject" :selectContent="selectContent" :selectWidth="selectWidth"
                         @changeSelect="cS"/>
        <img src="./assets/logo.png">
        <HelloWorld/>
        <paginate :curr="1" :all="10"/>
        <button @click="showToast()">点击显示Toast</button>
        <toast :message='JSON.stringify("细思极恐")' :time="3000" ref="$Message"/>
    </div>
</template>

<script>
    import HelloWorld from './components/HelloWorld'
    import selectComponent from './components/selectComponent'
    import paginate from './components/paginate'
    import toast from './components/toast'

    export default {
        name: 'App',
        data() {
            return {
                subject: [{index: 0, text: "吃饭"}, {index: 1, text: "睡觉"}, {index: 2, text: "打豆豆"}],
                selectContent: {
                    value: 0,
                    text: "点击选择"
                },
                selectWidth: 200
            }
        },
        methods: {
            cS(a, b) {
                console.log(a);
                console.log(b);
            },
            showToast() {
                // this.$refs.toastUI.$emit('childMethod');
                this.$refs.$Message.init()
            }
        },
        components: {
            HelloWorld,
            selectComponent,
            paginate,
            toast
        }
    }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
