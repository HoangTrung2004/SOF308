<template>  
<h1>{{ name }}</h1>
    <h2>Number: {{ count }}</h2>
    <button @click="increment">Cộng</button>
    <button @click="decreasing">Trừ</button>
    <button @click="reset">Reset</button>
</template>

<script>
    export default {
        data() {
            return {
                count: 22,
                name: "Trung"
                
            };
        },
        methods: {
            increment(){
                this.count++;
            },
            decreasing(){
                this.count--;
            },
            reset() {
                this.count = 0; 
            }
        }
    }
</script>