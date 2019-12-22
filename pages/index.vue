<template>
  <div class="container">
    <h1>User Blog Posts</h1>
    <div class='posts'>
        <div v-for="post in posts" class="post">
            <h1>{{post.title}}</h1>
            <a :href="post.user"><h3>Author: {{post.user}}</h3></a>
            <h3>Featured Tech: {{post.tech}}</h3>
            <button v-on:click="switchShow(post._id)">Show</button>
            <p v-if="switches[post._id]">{{post.entry}}</p>

    </div>
    </div>
  </div>
</template>

<script>

// const getPosts = async () => {
//     const url = 'https://wrfjnsifxl.execute-api.us-east-1.amazonaws.com/production/api/blogs/'
//     const response = await fetch(url)
//     const json = await response.json()
//     console.log(json)
//     return await json
//   }
//
// const thePosts = getPosts();


export default {
    async asyncData({ $axios }) {
    const posts = await $axios.$get('https://wrfjnsifxl.execute-api.us-east-1.amazonaws.com/production/api/blogs/')
    const switches = {}
    posts.forEach((post) => switches[post._id] = false)
    return { posts, switches }
    },
    methods: {
        switchShow: function (id) {
            this.switches[id] = !this.switches[id];
        //     if (this.switches.id == true){
        //         this.$set(this.switches, id, false)
        //         console.log('false')
        //     } else {
        //         this.$set(this.switches, id, true)
        //         console.log('true')
        //     }
        }
    }

  // async asyncData ({ params }) {
  //   const user = params.users // When calling /abc the slug will be "abc"
  //   return { user }
  // }

}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Mada&display=swap');

.container {width: 80%; background-color: #cee0dc; padding: 10px; margin: 10px auto; font-family: 'Mada', sans-serif; border-radius: 10px;}

.container h1 {color: #A5243D; text-transform: uppercase;}

.post {background-color: white; border-radius: 10px; margin: 10px; padding:10px;}

.post h1 {color: black;}

.post h3 {background-color: #A5243D; color: white; max-width: 200px; margin: 10px auto; padding: 5px}

.post p {text-align: left; padding: 20px; font-size: 120%; width: 70%; margin: 10px auto;}

button {margin: 20px; padding: 10px; text-transform: uppercase; width: 100px; background-color:#A5243D;
        color: white; border: none; transition: color .4s, background-color .4s;}

button:hover {background-color: white; color: #A5243D; }

</style>
