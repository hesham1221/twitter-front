<template>
    <div class="writeATweet">
                <img src="../assets/batman.png">
                <h3>Lorem ipsum dolor sit amet consectetur adipisicing elit. Perferendis deleniti in ducimus? Voluptatum labore commodi exercitationem eos, consequuntur quidem magnam. Labore illo corporis neque delectus repellat ullam, id culpa distinctio!</h3>
            </div>
            <button>Tweet</button>
</template>

<style lang="scss">
    .main-container{
        padding: 20px 20px 0 20px;
        display: flex;
        flex-direction: column;
        flex : 0.4  ;
        border-right: 1.5px rgb(44, 44, 44) solid;
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
            h3{
                width: 100%;
                background-color: transparent;
                border: 0;
                font-size: 23px;
            }
        }
    }
</style>