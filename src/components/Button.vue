<template>
    <button class="button">{{content}}</button>
</template>

<script>
export default {
    name : 'Button',
    props : {
        content : String,
        color : String
    },

}
</script>
<style lang="scss">
    .button{
        border: none;
        padding: 13px 13px ;
        width: 50%;
        border-radius: 30px;
        font-size: 17px;
        cursor: pointer;
        &:first-of-type{
            background-color: #1A8CD8;
            color :white
        }
        &:first-of-type:hover{
            background-color: darken(#1A8CD8 , 4);
        }
        &:nth-of-type(2):hover{
            background-color: darken(rgb(236, 235, 235) , 4);
        }
    }
</style>