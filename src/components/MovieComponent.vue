<template>

<div class="card" style="width: 20rem;">
  <img :src="imageUrl" class="card-img-top" />
  <div class="card-body">
  <h5 class="card-title">{{ title }}</h5>
  <h6 class="card-subtitle mb-2 text-muted">{{ rating }} | {{ length }} mins</h6>
  <div class="btn btn-info"><router-link :to="'/movie-details/' + this.id">View</router-link></div>
  <div class="btn btn-info"><router-link :to="'/movie-details/' + this.id + '/rentals'">Rentals</router-link></div>
</div>
</div>
</template>

<script>
export default {
    data () {
      return {}
    },
    methods: {
      view () {
        // this.$emit('view', this.id);
        console.log('Component Viewing id:' + this.id)

        // this.$router.push({ name: 'customer-details', params: { id: 3 } })
        let myRoute = '/movie-details/' + this.id;
        this.$router.push(myRoute);
      },
      rentals () {
        this.$emit('rentals', this.id);
      }
    },
    computed: {
        /* Build URL for image */
        imageUrl: function(){
          return   "http://codeflare.tech/images/movie_" + this.id + ".jpg";
        }
      },
    props: ['id', 'title', 'rating', 'length', 'onDVD', 'onBluRay']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

  .btn-info {
    text-align: center;
    margin-top: 20px;
  }

  .card {
    margin-bottom: 15px;
    padding-bottom: 3px;
    background-color: #dee5ef;
  }

</style>
