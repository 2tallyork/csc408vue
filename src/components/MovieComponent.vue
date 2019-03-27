<template>
    <tr>
        <td>{{ img }}</td>
        <td>{{ title }}</td>
        <td>{{ rating }}</td>
        <td>{{ length }}</td>
        <td>{{ description }}</td>
        <td>
            <div class="btn btn-sm btn-success"><router-link :to="'/movie-details/' + this.id">View</router-link></div>
            <div class="btn btn-sm btn-dark"><router-link :to="'/movie-details/' + this.id + '/rentals'">Rentals</router-link></div>
        </td>
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
    props: ['id', 'title', 'rating', 'length', 'description']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
