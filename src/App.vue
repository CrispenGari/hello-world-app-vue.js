<template>
  <div class="app">
    <User
      :tweets="tweets"
      :user="user"
      :options="options"
      :submitTweet="submitTweet"
      @user_tweet="submitTweet"
    />
    <Main :tweets="tweets" :deleteTweet="deleteTweet" />
  </div>
</template>

<script>
import { Main, User } from "./components";
export default {
  name: "App",
  components: {
    User,
    Main,
  },
  data() {
    return {
      age: 24,
      message: "",
      user: {
        username: "username",
        name: "Name",
        surname: "Surname",
        age: 24,
        followers: 5,
      },

      options: [
        { id: 1, value: true, name: "Admin" },
        { id: 2, value: false, name: "Not Admin" },
      ],
      tweets: [
        {
          id: 1,
          username: "username",
          tweet: "This is a tweet 1",
          isAdmin: true,
        },
        {
          id: 2,
          username: "username1",
          tweet: "This is a tweet 2",
          isAdmin: false,
        },
        {
          id: 3,
          username: "username2",
          tweet: "This is a tweet 3",
          isAdmin: false,
        },
        {
          id: 4,
          username: "username3",
          tweet: "This is a tweet 4",
          isAdmin: true,
        },
      ],
    };
  },
  methods: {
    submitTweet(user_tweet) {
      console.log(user_tweet);
      return this.tweets.unshift(user_tweet);
    },
    deleteTweet(id) {
      this.tweets = this.tweets.filter((tweet) => tweet.id !== id);
    },
  },

  mounted() {},
};
</script>

<style scoped>
.app {
  display: flex;
  width: 100%;
  max-width: 600px;
  margin: 10px auto;
}
</style>
