<template>
    <h1> {{ greeting }}</h1>
    <button v-bind:title="buttonTitle" @click="changeGreeeting">Nhấp để thay đổi</button>
</template>

<script>
    export default {
        data (){
            return {
                greeting: "Xin chào bạn",
                buttonTitle: "Nhấp vào để thay đổi lời chào",
            };
        },
        methods: {
            changeGreeeting() {
                this.greeting = "Hello, World!!!!!!!!!!!";
                this.buttonTitle = "Lời chào mới đã được cập nhật";
            }
        }
        }
</script>