<template>
  <div class="user">
    <div class="user__user">
      <h1>
        @{{ user?.username }} <span v-if="admin">{{ "Admin" }}</span>
        <span v-else>{{ "Not Admin" }}</span>
      </h1>
      <p>
        Followers: <span>{{ followersCount }}</span>
      </p>
      <p>
        Full Name: <span>{{ fullName }}</span>
      </p>
      <p>
        Age: <span>{{ user?.age }}</span>
      </p>
      <p>
        YOB: <span>{{ yearOB }}</span>
      </p>
    </div>
    <form class="user__form">
      <textarea
        cols="30"
        rows="4"
        class="user__form__textarea"
        placeholder="type a message..."
        v-model.trim="message"
      >
      </textarea>
      <select class="user__form__select" v-model="isAdmin">
        <option
          v-for="option in options"
          :key="option?.id"
          :value="option?.value"
        >
          {{ option?.name }}
        </option>
      </select>
      <button
        :disabled="!message"
        type="submit"
        class="user__form__b"
        @click.prevent="submitTweet"
      >
        Submit
      </button>
    </form>
  </div>
</template>

<script>
export default {
  name: "User",
  data() {
    return { isAdmin: false, message: "" };
  },
  props: {
    user: Object,
    options: Array,
    tweets: Array,
  },

  computed: {
    followersCount() {
      return this.user.followers;
    },
    fullName() {
      return `${this.user.name} ${this.user.surname}`;
    },
    yearOB() {
      return 2021 - this.user.age;
    },
    admin() {
      return this.isAdmin;
    },
  },
  methods: {
    submitTweet() {
      const user_tweet = {
        username: this.user?.username,
        isAdmin: this.isAdmin,
        tweet: this.message,
        id: this.tweets?.length + 1,
      };
      this.$emit("user_tweet", user_tweet);
      this.message = "";
    },
  },
};
</script>

<style scoped>
.user {
  background-color: white;
  border-radius: 5px;
  border: 1px solid lightgray;
  padding: 10px;
  flex: 0.5;
  margin: 5px;
  height: fit-content;
}
.user__user > h1 {
  display: flex;
  width: 100%;
  justify-content: space-between;
  align-items: center;
  font-size: 15px;
  color: gray;
}
.user__user > h1 > span {
  background: black;
  color: white;
  margin: 10px;
  padding: 2px 5px;
  border: none;
  outline: none;
  border-radius: 5px;
  font-size: 10px;
}
.user__user > p {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 14px;
  width: 100%;
  color: gray;
  padding: 5px 0;
}
.user__form {
  padding: 10px 0 0 0;
  margin: 10px 0 0 0;
  border-top: 1px solid lightgray;
}
.user__form__select {
  outline: none;
  border: none;
  background: #f5f5f5;
  width: 100%;
  margin: 10px auto;
  padding: 2px;
}
.user__form__b {
  width: 90px;
  outline: none;
  border: none;
  cursor: pointer;
  background: #000000;
  color: white;
  border-radius: 5px;
  padding: 3px;
}
.user__form__textarea {
  resize: none;
  outline: none;
  border: none;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  background: #f5f5f5;
  padding: 5px;
  border-radius: 5px;
  caret-color: blue;
  width: 100%;
}
</style>
