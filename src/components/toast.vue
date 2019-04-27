<template>
    <div id="toastDiv">
        <span class="message">{{message}}</span>
    </div>
</template>

<script>
    export default {
        name: "toast",
        components: {},
        props: {
            message: {
                type: String,
                default: ""
            },
            time: {
                type: Number,
                default: 3000
            }
        },
        data() {
            return {
                odiv: "",
                css: {
                    // width: this.message.length <= 6 ? this.message.length * 2 + "px" : "auto",
                    width: "auto",
                    height: this.message.length <= 10 ? Math.ceil(this.message.length / 10) * 20 + "px" : 20 + "px",
                    backgroundColor: "rgba(0, 0, 0, .8)",
                    padding: "4px",
                    margin: this.width ? "0 -" + this.width.split("px")[0] / 2 + "px" : "5px",
                    position: "fixed",
                    left: "50%",
                    bottom: "50%",
                    zIndex: "999",
                    textAlign: "center",
                    borderRadius: "5px",
                    display: "block",
                    verticalAlign: "middle"
                }
            }
        },
        mounted: function () {
            // console.log(this.message.length);

            // document.getElementsByTagName('body')[0].appendChild()
            this.odiv = document.getElementById("toastDiv");
            // this.$on('childMethod', function () {
            //     alert("进来了");
            // });
            // this.init();
        },
        methods: {
            init: function () {
                for (var property in this.css) {
                    this.odiv.style[property] = this.css[property];
                }
                this.stot();
            },
            stot: function () {
                var that = this;
                setTimeout(function () {
                    that.odiv.style.display = "none";
                }, that.time || 3000)
            }
        }
    }
</script>

<style>
    #toastDiv .message {
        color: #fff
    }
</style> 
