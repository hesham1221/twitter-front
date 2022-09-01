<template>
<div class="contRIght">
    <img class="twitterRight" src="../assets/twitter-icon-blue.svg" />
    <div class="header">
        <h1>Happening now</h1>
        <h2>Join Twitter today.</h2>
        <h3>Twitter clone</h3>
        <p>made with ❤️ by hesham in <a target="_blank" href="https://www.baianat.com/">Baianat</a></p>
    </div>
    <div class="controls">
        <Button @onClick="$emit('show' ,'Sign Up')" content = 'Sign Up' />
        <Button @onClick="$emit('show' , 'Sign In')" content = 'Sign In' />
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
            Button,
        },
        methods :{
           
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
        h2{
            margin-bottom:20px ;
        }
        h3{
            margin-bottom: 10px;
        }
        p{
            a {
                color :#1A8CD8;
                text-decoration: none;
                &:hover{
                    color: lighten(#1A8CD8 , 4);
                }
            }
        }
        .controls{
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            min-height:120px ;
        }
    }
</style>