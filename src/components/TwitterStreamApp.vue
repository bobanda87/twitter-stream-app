<template>
  <div class="tweets">
    <h1>Twitter streaming app</h1>
    <div class="container">
      <div class="row">
        <div class="col-md-12">
          <table class="table table-striped">
            <thead>
            <tr>
              <th scope="col">User</th>
              <th scope="col">Tweet</th>
              <th scope="col">Retweet count</th>
              <th scope="col">Reply count</th>
              <th scope="col">Favorite count</th>
            </tr>
            </thead>
            <tbody>
            <tr class="tweet" v-for="tweet in tweets" v-bind:key="tweet">
              <th scope="row">
                <span><img :src="tweet.profileImage" :alt="tweet.userName"/></span>
                <span>{{ tweet.userName }}</span>
              </th>
              <td class="align-middle">
                <span>{{ tweet.text }}</span>
              </td>
              <td class="align-middle">
                <span>{{ tweet.retweetCount }}</span>
              </td>
              <td class="align-middle">
                <span>{{ tweet.replyCount }}</span>
              </td>
              <td class="align-middle">
                <span>{{ tweet.favoriteCount }}</span>
              </td>
            </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Pusher from 'pusher-js' // import Pusher

export default {
  name: 'TwitterStreamApp',
  // props: {
  //   msg: String
  // },
  data () {
    return {
      tweets: []
    }
  },
  created () {
    this.subscribe()
  },
  methods: {
    subscribe () {
      let pusher = new Pusher('c92eaf445c270f4c2e86', { cluster: 'eu' })
      pusher.subscribe('twitter-stream')
      pusher.bind('tweets', data => {
        console.log(data);
        this.tweets.unshift(data);
      })
    }
  },
}
</script>

<style>
.tweet img {
  border-radius: 50%;
  width: 60px;
  height: 60px;
  margin: 10px;
}
</style>
