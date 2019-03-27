<template>
    <tr>
        <td><img :src="imageUrl" style="width: 75px;" /></td>
        <td>{{ title }} <br /><br />
        <div class="btn btn-sm btn-success"><router-link :to="'/movie-details/' + this.id">View</router-link></div>
        <div class="btn btn-sm btn-dark"><router-link :to="'/movie-details/' + this.id + '/rentals'">Rentals</router-link></div>
</td>
        <td>{{ rating }}</td>
        <td>{{ length }}</td>

    </tr>
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
        let myRoute = '/movie-details/3';
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
    props: ['id', 'title', 'rating', 'length', 'onDvd', 'onBluRay']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
