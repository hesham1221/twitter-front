<template>
    <div class="grey">
        <div class="modal">
            <h1>{{title}}</h1>
            <input type="text" placeholder="Username..." />
            <input type="password" placeholder="Password..." />
            
        </div>
    </div>
</template>

<script>
    export default {
        name :'Modal',
        props :{
            title : String
        }
    }
</script>
<style lang="scss">
    .grey{
        position: absolute;
        width: 100vw;
        height: 100vh;
        color: rgba(128, 128, 128, 0.089);
        display: grid;
        place-content: center;

        .modal{
            background-color: black;
            display: flex;
            flex-direction: column;
        }
    }
</style>