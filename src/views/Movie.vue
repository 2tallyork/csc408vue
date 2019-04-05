<template>
    <div class="about pt-4 pb-3">
        <h1 class="page-header">MOVIES</h1>
<hr>
<div class="container">
<div class="content">
<div class="row">
            <movie-component
                    v-for="(movie, index) in movies"
                    v-bind="movie"
                    :index="index"
                    :key="movie.id"
                    @view="view"
                    @rentals="rentals"
            ></movie-component>
            </tbody>
        </table>
    </div>
    </div>
    </div>
    </div>
</template>
<script>

  function Movie ({ id, title, rating, length, onDVD, onBluRay }) {
    this.id = parseInt(id)
    this.title = title
    this.rating = rating
    this.length = length
    this.onDVD = onDVD
    this.onBluRay = onBluRay
  }

  /* Go get the code for the movie-component tag that is in the template */
  import MovieComponent from '@/components/MovieComponent.vue'

  export default {
    data () {
      return {
        movies: []
      }
    },
    methods: {
      read () {
        this.movies = []
        window.axios.get('https://spenceryork.com/api/movies').then(({ data }) => {
          data.forEach(movie => {
                this.movies.push(new Movie(movie))
            })
        })
      },
      view (id) {
      },
      rentals (id) {
      }
    },
    components: {
      MovieComponent
    },
    created () {
      this.read()
    }
  }
</script>

<style>
hr {
  border: 1px solid;
  border-color: #dee5ef;
  margin-bottom: 40px;
}

@import url('https://fonts.googleapis.com/css?family=Oswald:300,400');
.page-header {
  font-family: 'Oswald:300', sans-serif;
  font-size: 100px;
  color: #b3b7bf;
  margin: 0px;
  padding: 0px;
  letter-spacing: 75px;
}

</style>
