<template>
  <div>
    <a href="https://www.devnursery.com"><h1 class="logo"><span>dev</span>Nursery</h1></a>
    <nuxt />
    <h4>This application is made by Alex Merced of AlexMerced.com using Vue/Nuxt</h4>
  </div>

</template>

<style>
@import url('https://fonts.googleapis.com/css?family=Major+Mono+Display&display=swap');

body {
    text-align: center;
    padding: 20px;
    }

.logo {
        text-align: center;
        font-size: 300%;
        width: 100%;
        margin: 10px auto;
        font-family: 'Major Mono Display', monospace;
    }

.logo span {
        color: #A5243D;
    }

a {text-decoration: none; color: black;}

@media only screen and (max-width: 500px) {
  .logo {font-size: 175%;}
}

</style>
