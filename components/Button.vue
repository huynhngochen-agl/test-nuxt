<template>
    <button v-on:click="changeText">{{data}}</button>
</template>

<script>
export default {
    name: 'button',
     data(){
        return {
            data: "Want to play?",
        }
    },
    methods: {
        changeText(e){
            this.data = "I am working!"
        }
    }
}
</script>