<template>
  <div class="tweet">
    <h1>
      @{{ tweet?.username }} <span v-if="tweet?.isAdmin">Admin</span
      ><span v-else>Not Admin</span>
    </h1>
    <p>{{ tweet?.tweet }}</p>
    <button @click="deleteTweet(tweet.id)">delete</button>
  </div>
</template>

<script>
export default {
  name: "Tweet",
  props: {
    tweet: Object,
    deleteTweet: Function,
  },
  methods: {},
};
</script>

<style scoped>
.tweet {
  padding: 5px;
  border-radius: 5px;
  border: solid 1px lightgray;
  margin: 5px 0;
  width: 100%;
  background: #f5f5f5;
}
.tweet > h1 {
  display: flex;
  width: 100%;
  justify-content: space-between;
  align-items: center;
  font-size: 15px;
  color: gray;
}
.tweet > p {
  font-size: 12px;
  user-select: none;
  padding: 5px 0;
}
.tweet > h1 > span {
  background: black !important;
  color: white;
  margin: 10px;
  padding: 2px 5px;
  border: none;
  outline: none;
  border-radius: 5px;
  font-size: 10px;
}
.tweet > button {
  width: 90px;
  outline: none;
  border: none;
  cursor: pointer;
  background: #000000;
  color: white;
  border-radius: 5px;
  padding: 3px;
}
</style>
