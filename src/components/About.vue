<template>
  <div class="about">
    <h1>Hello Everyone, this is Divya's page</h1>
    <p>Hello Everyone, This is Divya Korrapati. I am currently pursuing my Master's in Management Information Systems at UNO.</p>
    <p> I love making some delicious Indian dishes whenever I get some time and I am also passionate about learning all the gymnastic skills at CrossFit.</p> 
    <p>I will be the happiest person on earth if someone drops into my home surprisingly and gets to taste my dishes!!.</p>
  </div>
</template>
<script>
export default {
  name: 'About',
  data() {
    return {
      their_name: this.$route.params.name
    }
  }
}
</script>