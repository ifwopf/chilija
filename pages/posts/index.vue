<template>
  <div>
    <div id="container">
      <div class="quadrat">
        <p class="uberhead">Chilija</p>
        <nuxt-link v-for="post in posts" :key="post.attributes.title" class="tag"
                   :to="'/posts/'+ post.attributes.title">
          {{post.attributes.title}}
        </nuxt-link>
      </div>
    </div>
  </div>
</template>
<script>
  export default {
    async asyncData() {
      const resolve = require.context("~/content/", true, /\.md$/);
      const imports = resolve.keys().map((key) => {
        const [, name] = key.match(/\/(.+)\.md$/);
        return resolve(key);
      });
      return {
        posts: imports
      }
    },
  }
</script>

<style scoped>
  * {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
  }

  html {
    font-family: "Lacida sans Unicode", sans-serif;
    margin: 0;
    background-color: lavender;
    -moz-user-select: auto;
    cursor: auto;
  }

  body {
    text-align: center;
  }

  h1, h2, h3 {
    margin: 0.2vw;
    background-color: #fff;
  }

  p {
    margin: 0;
  }

  a .tag, .uberhead {
    color: black;
    text-decoration: none;
    display: inline-block;
  }

  a {
    color: #ff0065;
    text-decoration: none;
    display: inline-block;
  }

  img {
    margin: 10px auto;
    max-width: 100%;
    display: block;
  }

  #container {
    text-align: left;
    margin-top: 5px;
    margin-bottom: 5px;
  }

  .content {
    margin: 1vw auto;
    max-width: 600px;
    background-color: #fff;
    padding: 5px 6px 5px 8px;
    display: block;
  }

  .img_content {
    margin: 1vw auto;
    background-color: #fff;
    padding: 5px 6px 5px 8px;
    display: block;
  }

  .quadrat {
    margin: 10px auto;
    max-width: 600px;
  }

  .uberhead {
    font-size: 200%;
    font-weight: bold;
    background-color: #fff;
    padding: 2px 3px 2px 3px;
    display: inline;
    margin: 0;
  }

  .tag {
    font-weight: bold;
    background-color: #fff;
    display: inline-block;
    padding: 2px 3px 2px 3px;
    margin: 1vw 0 0 0;
  }

  #blue {
    background-color: #F3F315
  }

  pre {
    background-color: black;
    color: white
  }

  ul {
    list-style-type: square;
  }

  table, th, td {
    border: none;
    padding: 4px;
    margin: 2px;
    text-align: center;
  }

  table {
    display: inline;
  }

  th {
    background-color: #fff;
  }

  .zitat {
    background-color: #ffcb00;
    font-style: italic;
    padding: 5px;
    margin-left: 15px;
    margin-right: 10px;
    margin-top: 15px;
    margin-bottom: 15px;
  }
</style>
