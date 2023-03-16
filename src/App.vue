<template>
  <div>
    <div class="buttons">
      <button @click="Get">Get</button>
      <button @click="GetAll">Get All</button>
      <button @click="Post">Post</button>
      <button @click="Put">Put</button>
      <button @click="Patch">Patch</button>
      <button @click="Delete">Delete</button>
    </div>

    <div v-if="button === 1" class="Get">
      <h2>{{ this.posts.id }} {{ this.posts.title }}</h2>
      <p>{{ this.posts.body }}</p>
    </div>

    <div v-if="button === 2" class="GetAll">
      <div v-for="post in posts" :key="post.id">
        <h2>{{ post.id }} {{ post.title }}</h2>
        <p>{{ post.body }}</p>
      </div>
    </div>

    <div v-if="button === 3" class="Post">
      <h2>{{ this.posts.id }} {{ this.posts.title }}</h2>
      <p>{{ this.posts.body }}</p>
    </div>

    <div v-if="button === 4" class="Put">
      <h2>{{ this.posts.id }} {{ this.posts.title }}</h2>
      <p>{{ this.posts.body }}</p>
    </div>

    <div v-if="button === 5" class="Patch">
      <h2>{{ this.posts.id }} {{ this.posts.title }}</h2>
      <p>{{ this.posts.body }}</p>
    </div>
    <div v-if="button === 6" class="Delete">
      <h2>{{ this.posts.id }} {{ this.posts.title }}</h2>
      <p>{{ this.posts.body }}</p>
    </div>

  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      posts: [],
      button: 0
    }
  },
  mounted() {

  },
  methods: {
    Get() {
      this.button = 1
      axios.get('https://jsonplaceholder.typicode.com/posts/1')
        .then(response => {
          this.posts = response.data
          console.log(this.posts)
        })
    },
    GetAll() {
      this.button = 2
      axios.get('https://jsonplaceholder.typicode.com/posts')
        .then(response => this.posts = response.data)
    },
    Post() {
      this.button = 3
      axios.post('https://jsonplaceholder.typicode.com/posts', {
        userId: '1',
        title: 'Post Title',
        body: 'Post Body Content'
      })
        .then(response => this.posts = response.data)
    },
    // Specify All Content for Update
    Put() {
      this.button = 4
      axios.put('https://jsonplaceholder.typicode.com/posts/1', {
        id: 1,
        userId: '1',
        title: 'Post Title',
        body: 'Post Body Content'
      })
        .then(response => {
          console.log(response)
          this.posts = response.data
        })
    },
    // Only Update Certain Values
    Patch() {
      this.button = 5
      axios.patch('https://jsonplaceholder.typicode.com/posts/1')
        .then(response => {
          console.log(response)
          this.posts = response.data
        })
    },
    Delete() {
      this.button = 6
      axios.delete('https://jsonplaceholder.typicode.com/posts/1')
        .then(response => {
          console.log(response)
          this.posts = response.data
        })
    },
  }
}
</script>

<style></style>
