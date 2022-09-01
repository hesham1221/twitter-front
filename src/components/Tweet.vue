<template>
  <div class="tweetCont">
    <div class="writeATweet">
      <img :src="'https://robohash.org/' + tweet.author.username" />
      <div class="text">
        <div class="info">
          <span class="author">{{ tweet.author.username }}</span>
          <span class="date">{{ date }}</span>
        </div>
        <h3>
          {{ tweet.content }}
        </h3>
      </div>
    </div>
    <div class="actions">
      <i
        @click="like"
        :class="[liked ? 'liked' : '', 'heart', 'fa', 'fa-heart']"
      ></i>
      <span>{{tweet.likers.length }}</span>
    </div>
  </div>
</template>

<script>
export default {
  created() {
    const days = [
      "Sunday",
      "Monday",
      "Tuesday",
      "Wednesday",
      "Thursday",
      "Friday",
      "Saturday",
    ];
    const d = new Date(this.tweet.createdAt);
    var dayName = days[d.getDay()];
    const allhours = d.getHours()
    let hoursAndMinutes = ''
    if (allhours > 12){
        hoursAndMinutes = `${allhours - 12}:${d.getMinutes()} pm   ( ${d.getDate()}/${d.getMonth()}/${d.getFullYear()} )`
    }else{
        hoursAndMinutes = `${allhours}:${d.getMinutes()} am  ( ${d.getDate()}/${d.getMonth()}/${d.getFullYear()} )`
    }
    this.date = `${dayName} at ${hoursAndMinutes}`
  },
  data() {
    return {
      likers: 23,
      liked: false,
      date: "",
    };
  },
  methods: {
    like() {
      this.liked = !this.liked;
      
      if (this.liked) {
        this.tweet.likers.push({username : this.user.username});
      } else {
        this.tweet.likers = this.tweet.likers.filter(liker => liker.user === this.user.username)
      }
    },
  },
  props: {
    tweet: Object,
    user :Object
  },
};
</script>

<style lang="scss">
.tweetCont {
  display: flex;
  flex-direction: column;
  padding: 12px 9px;
  border-bottom: 1.5px rgb(44, 44, 44) solid;
  .info {
    padding: 9px 0;
    .author {
      font-weight: 700;
      margin-right: 9px;
    }
    .date {
      color: rgba(94, 89, 89, 0.829);
    }
  }
}
button {
  border: none;
  padding: 13px 9px;
  background-color: #1a8cd8;
  width: 150px;
  align-self: center;
  border-radius: 30px;
  font-size: 17px;
  cursor: pointer;
  margin-bottom: 30px;
}
.actions {
  align-self: flex-end;
  display: flex;
  align-items: center;
  .liked {
    color: red;
  }
}
.heart {
  margin-right: 9px;
  font-size: 25px;
  color: rgba(255, 255, 255, 0.164);
  cursor: pointer;
  &:hover {
    color: red;
  }
}
.writeATweet {
  display: flex;
  padding: 20px 20px 20px 0;
  img {
    width: 55px;
    height: 66px;
    border-radius: 30px;
    margin-right: 30px;
    align-self: center;
  }
  h3 {
    width: 100%;
    background-color: transparent;
    border: 0;
    font-size: 17.5px;
    font-weight: 400;
  }
}
</style>
