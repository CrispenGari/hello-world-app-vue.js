<template>
  <div class="main">
    <Tweet
      :deleteTweet="deleteTweet"
      v-for="tweet in tweets"
      :key="tweet?.id"
      :tweet="tweet"
    />
  </div>
</template>

<script>
import { Tweet } from "../../components";
export default {
  name: "Main",
  components: { Tweet },
  props: {
    tweets: Object,
    deleteTweet: Function,
  },
};
</script>

<style scoped>
.main {
  background-color: white;
  border-radius: 5px;
  border: 1px solid lightgray;
  padding: 10px;
  flex: 0.5;
  margin: 5px;
  height: fit-content;
}
</style>
