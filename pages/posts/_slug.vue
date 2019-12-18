<template>
    <div id="container">
      <div class="quadrat">
        <p id="titel" class="uberhead" v-html="post.attributes.title"></p>
        <p id="author" class="info" v-html="post.attributes.author"></p>
        <p id="datum" class="info" v-html="post.attributes.date"></p>
        <p id="ort" class="info" v-html="post.attributes.location"></p>
      </div>
      <div class="content" v-html="post.html">
      </div>
      <div class="quadrat">
        <p v-for="tag in post.attributes.tags" class="tag" v-html="tag"></p>
      </div>
  </div>
</template>
<script>
  export default {
    async asyncData({ params }) {
      try {
        let post = await import(`~/content/${params.slug}.md`);
        console.debug(post);
        return {
          post
        }
      } catch(err) {
        console.debug(err);
        return false
      }
    }
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

  h1, h2, h3 {margin: 0.2vw;
    background-color: #fff;
  }

  p {
    margin: 0;
  }

  a .tag, .uberhead{color: black;
    text-decoration: none;
    display: inline-block;}

  a {color: #ff0065;
    text-decoration: none;
    display: inline-block;}

  img {margin: 10px auto;
    max-width: 100%;
    display:block;
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
    text-transform: uppercase;
    padding: 2px 3px 2px 3px;
    display: inline;
    margin: 0;
  }
  .info {
    background-color: #fff;
    color: #000;
    display: inline-block;
    padding: 2px 3px 2px 3px;
    margin: 1vw 0 0 0;
  }

  .tag {
    background-color: #000;
    color: #fff;
    display: inline-block;
    padding: 2px 3px 2px 3px;
    margin: 1vw 1vw 0 0;
  }

  #blue {background-color: #F3F315}

  pre {background-color: black;
    color: white}

  ul {
    list-style-type: square;
  }

  table, th, td {
    border: none;
    padding: 4px;
    margin: 2px;
    text-align: center;
  }

  table {display: inline;}

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
