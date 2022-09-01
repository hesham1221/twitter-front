<template>
  <div class="main-container">
    <div class="top">
      <h2>Home</h2>
      <div class="writeATweet">
        <img :src="'https://robohash.org/' + user.username" />
        <input
          :value="content"
          @change="content = $event.target.value"
          placeholder="Whats happening?...."
        />
      </div>
      <button @click="tweet">Tweet</button>
    </div>
    <div class="center">
      <Tweet :user="user" v-for="tweet in Tweets" :tweet="tweet" />
    </div>
  </div>
</template>

<script>
import Tweet from "./Tweet.vue";
import axios from "axios";

const token = localStorage.getItem("baianat-twitter");

export default {
  components: {
    Tweet,
  },
  props: {
    user: Object,
  },
  created() {
    this.getTweets();
  },
  data() {
    return {
      content: "",
      Tweets: [],
    };
  },
  methods: {
    async tweet() {
      try {
        await axios({
          url: "http://192.168.50.22:5000/graphql",
          method: "POST",
          headers: {
            Authorization: "Bearer " + token,
          },
          data: {
            query: `
                    mutation {
  createATweet(createTweetInput :{
    content: "${this.content}"
  }){
    content
    id
  }
}
                    `,
          },
        });
        this.Tweets.push({
          content: this.content,
          createdAt: Date.now(),
          likers: [],
          author: {
            username: this.user.username,
          },
        });
        this.content = "";
      } catch (error) {
        console.log(error);
      }
    },
    async getTweets() {
      try {
        const res = await axios({
          url: "http://192.168.50.22:5000/graphql",
          method: "POST",
          data: {
            query: `{
  tweets{
    content
    createdAt
    id
    likers{
      username
    }
    author{
      username
    }
  }
}`,
          },
        });
        const fetchedTweet = res.data.data.tweets;
        this.Tweets = [...fetchedTweet];
      } catch (error) {}
    },
  },
};
</script>
<style lang="scss">
.main-container {
  padding: 20px 20px 0 20px;
  display: flex;
  flex-direction: column;
  flex: 0.534;
  border-right: 1.5px rgb(44, 44, 44) solid;
  .center {
    overflow-y: scroll;
    &::-webkit-scrollbar {
      color: transparent;
    }
  }
  .top {
    display: flex;
    flex-direction: column;
    border-bottom: 1.5px rgb(44, 44, 44) solid;
  }
  button {
    border: none;
    padding: 13px 9px;
    background-color: #1a8cd8;
    width: 150px;
    align-self: flex-end;
    border-radius: 30px;
    font-size: 17px;
    cursor: pointer;
    margin-bottom: 30px;
  }
  .writeATweet {
    display: flex;
    padding: 20px 20px 20px 0;
    img {
      width: 55px;
      border-radius: 30px;
      margin-right: 30px;
    }
    input {
      width: 100%;
      background-color: transparent;
      border: 0;
      &:focus {
        outline: none;
      }
      font-size: 23px;
    }
  }
  h2 {
    font-size: 20px;
  }
}
</style>
