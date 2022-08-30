<template>
<div class="contRIght">
    <img class="twitterRight" src="../assets/twitter-icon-blue.svg" />
    <div class="header">
        <h1>Happening now</h1>
        <h2>Join Twitter today.</h2>
    </div>
    <div class="controls">
        <Button content = 'Sign Up' />
        <Button content = 'Sign In' />
    </div>
</div>
</template>

<script>
    import Button from './Button.vue'
    export default {
        name :"left",
        props :{

        },
        components :{
            Button
        }
    }
</script>

<style lang="scss">
    .contRIght{
        display: flex;
        flex-direction : column;
        justify-content: space-between;
        color : white;
        height: 100%;
        padding: 30px;
        .twitterRight{
            width: 40px;
        }
        h1{
            font-size: 60px;
            margin-bottom: 30px;
        }
        .controls{
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            min-height:120px ;
        }
    }
</style>