<template>
    <div class="main-container">
        <div class="top">
            <h2>Home</h2>
            <div class="writeATweet">
                <img src="../assets/batman.png">
                <input placeholder="Whats happening?...." />
            </div>
            <button>Tweet</button>
        </div>
        <div class="center">

        </div>
    </div>
</template>

<script>

export default{
    components :{
        
    }
}
</script>
<style lang="scss">
    .main-container{
        padding: 20px 20px 0 20px;
        display: flex;
        flex-direction: column;
        flex : 0.534 ;
        border-right: 1.5px rgb(44, 44, 44) solid;
        .top{
            display: flex;
            flex-direction: column;
            border-bottom: 1.5px rgb(44, 44, 44) solid;
        }
         button{
         border: none;
        padding: 13px 9px ;
        background-color: #1A8CD8;
        width: 150px;
        align-self: flex-end;
        border-radius: 30px;
        font-size: 17px;
        cursor: pointer;
        margin-bottom: 30px;
        }
        .writeATweet{
            display: flex;
            padding: 20px 20px 20px 0;
            img{
                width: 55px;
                border-radius: 30px;
                margin-right: 30px;
            }
            input{
                width: 100%;
                background-color: transparent;
                border: 0;
                &:focus{
                    outline: none;
                }
                font-size: 23px;
            }
        }
        h2{
            font-size: 20px
        }
    }
</style>