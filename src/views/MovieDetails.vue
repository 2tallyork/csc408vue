<template>
    <div class="pt-4 pb-3">

        <div class="movie-card" style="width: 85%;">
            <div class="movie-card-body">
<div class="row">
<div class="left-content">
                <img class="movie-card-img" :src="imageUrl" />
</div>
<div class="right-content">
                <h1 class="movie-card-title">{{ movie.title }}</h1>
                <h5 class="movie-card-text">Rating: {{ movie.rating }}</h5>
                <h5 class="movie-card-text">Length: {{ movie.length }} min</h5>
                                <p style="color: gray;">{{ movie.description }}</p>
</div>
</div>


            </div>
        </div>

    </div>
</template>
<script>

  export default {
    data () {
      return {
        id: null,
        movie: Object
      }
    },
    methods: {
      read (){
      console.log(this.id);
        let url = 'https://codeflare.tech/api/movies/' + this.id
        window.axios.get(url).then(({ data }) => {
          console.log(data);

          this.movie = data;
        })
      }
    },
    computed: {
      /* using the isAdmin, return a text role */
      imageUrl: function(){
        return   "http://codeflare.tech/images/movie_" + this.id + ".jpg";
      },
      role: function () {
            return this.movie.onBluRay ? 'Yes' : 'No';
            return this.movie.onDVD ? 'Yes' : 'No';
      },
      /* MAke a pretty date for showing last_update */
      updated: function(){
        var options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric', hour: 'numeric', minute: 'numeric' };
        var today  = new Date(this.movie.updated_at);
        return today.toLocaleString("en-US", options);
      }
    },
    components: {

    },
    created () {
      this.id = this.$route.params.movieId
      this.read()
    }
  }
</script>


<style>
@import url('https://fonts.googleapis.com/css?family=Montserrat:400,600');

    .right-content {
        width: 75%;
        padding-left: 15px;
    }
    .left-content {
      width: 25%;
      padding: 20px;
    }
    .movie-card-title {
      font-family: 'Montserrat:600', sans-serif;
      padding-top: 20px;
      padding-bottom: 5px;
    }
    .movie-card-text {
      display: block;
    }
    .movie-card {
        margin: auto;
      background-color: #dee5ef;
      border-radius: 20px;
    }
    .movie-card-body {
        text-align: left;
        margin: 10px;
    }

    img.movie-card-img {
      display: inline;
      padding: 10px;
      width: 250px;
      height: 350px;
    }
</style>
