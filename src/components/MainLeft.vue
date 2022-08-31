<template>
<div class="main-left">
    <div class="item">
        <img src="../assets/twitter-icon-white.svg" alt="twitter">
    </div>
    <div class="item">
        <img src="../assets/home.svg" alt="house">
        <h2>Home</h2>
    </div>
    <div class="item">
        <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIAAAAyCAYAAAAeP4ixAAAABmJLR0QA/wD/AP+gvaeTAAAArklEQVRoge3awQrCMBBF0YyfJf695rteVwUTU6iTRa71nZ2LKbkgNCOWYsYiqerTc3L+lT1PZAclafjAiFPPnJ3v3TJDRA6hcQiNQ2gcQtO8RSXVUsp90Vm+VSPisX/oQ4bXBqr368xlvloOoelD0vvAAs3u432ExiE0DqFxCI1DaLyPEHgfIbtsSF1yipxmd/I+QuMQGofQOITGITQzIaPrzOm/cBzM/9JPtvYfNiR2X1ZBaiMoAAAAAElFTkSuQmCC">
        <h2>Explore</h2>
    </div>
    <div class="item">
        <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAABmJLR0QA/wD/AP+gvaeTAAACKUlEQVRYhc2Xv2sUURSFzyzumqgomi0MiD8KRVCymGDUJrCIooKVSgjYCtqksIkbK20khaTSSvwDLAxBRAmIoCAkhZLCkARFDCpJTGIiadTis/CuTjE7mzdvZvHCa97ce87H3HlzeZJjAMeAu8AEsGprArgDHHXVyzkYF4EhScOSliVdlrTf1hVJ3yU9Ah4CLa4g9cx3Ae+Be8DmmLwtwH3gHbAzLfMNwDhwy6FmAHgDNKcBcB14Bri0Kwc8B675mueBJeBwgtpOYAFY5wNwHJj0qJ8GynE59V7rQUmjSQEkjZlGYoAWSUseAF8lFX0AFiRt8wAoSpr3AZiS1OEB0C5pOnE1UAAWgbYEtSU7BfnEACZ0E3jsWBMAT4AbXuYm1gxMARWHmn5gEmjyBjDBPcAn4HacqMEOWu7utMw3AhX7I84AH4E+oA3YZKtkezO2FoGrwHpf806bbCPVWQ+cBh4Ac/yLOds7ZTll4IXVHkpq3g2sAJeAoEZOU52W9ALLwHlX8wt2hLocuaO0ytaSM2st2Gf9jh0ijhAnTfNAvcQcMAb0pWUe0q4Ao7XaWU26CLz1/ntFa+ftozwXl/Qa6E7bPKTfA4zXelgC5oFChgAFO1l7q3vhaXhC0kgQBD+zAjDtp5LORgEckfQqK/NQvFRoxIcBdkj60ACAL5JaowC2SvrWAIBZSdujAPKSfjUA4Iekv0NqzZeNrOK/AvisP7ferGPFvCRJvwF7tQcCIJTiGwAAAABJRU5ErkJggg==">
        <h2>Profile</h2>
    </div>
    <Button content="Tweet" />
</div>
</template>

<script>
import Button from "./Button.vue";

export default {
    components :{
        Button
    }
}

</script>

<style scoped lang="scss">
    .main-left{
        display: flex;
        flex-direction: column;
        flex: 0.20;
        padding: 20px 40px;
        border-right: 1.5px rgb(44, 44, 44) solid;
        .item:first-of-type{
            &:hover{
                background-color:transparent;
                cursor: auto;
            }
            margin-bottom: 50px;
        }
        .item:last-of-type{
            margin-bottom: 30px;
        }
        .item{
            display: flex;
            width: 100%;
            align-items: center;
            cursor: pointer;
            margin-bottom: 9px;
            &:hover{
                color: #1a8cd8c4;
                h2{
                        color : #1a8cd8c4
                }
            }
            img{
                width: 50px;
                margin-right: 20px;
                padding: 15px 15px 15px 5px;
                color : black
            }
    
        }
    }
</style>