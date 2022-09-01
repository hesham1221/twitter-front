<template>
  <div class="author-cont">
    <img :src="'https://robohash.org/' + author.username" />
    <div class="info">
      <h3>{{author.username}}</h3>
      <span>follows: {{author.numFollowing}}</span><span>follower: {{author.numFollowers}}</span>
    </div>
    <button class="follow">follow</button>
  </div>
</template>

<script>

export default {
    props:{
        author : Object
    }
}
</script>

<style scoped lang="scss">
.author-cont {
    align-items: center;
    display: flex;
    width: 100%;
    padding: 5px;
    border-bottom:1.5px rgb(44, 44, 44) solid ;
    img{
    width: 55px;
    height: 66px;
    border-radius: 30px;
    margin-right: 30px;
    align-self: center;
    }

    .info{
        padding: 13px 14px 2px 10px;
        margin-bottom: 0;
        h3{
            margin-bottom: 5px;
        }
        span{
            margin-right: 13px;
            color: rgba(133, 130, 130, 0.829);
        }
    }

  .follow {
    border: none;
    padding: 13px 6px;
    width: 90px;
    border-radius: 30px;
    font-size: 17px;
    cursor: pointer;
    background-color: white;
    margin-top: 9px;
    margin-bottom: 0;
    color: #1A8CD8;
    font-size: 17px;
  }
}
</style>
