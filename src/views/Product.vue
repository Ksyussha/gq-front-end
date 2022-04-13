<template>
  <div>
    <h1>product</h1>
    <img :src="Products_by_pk?.Images[0].imageURL" alt="">
    <p>{{ Products_by_pk?.id }}</p>
    <p>{{ Products_by_pk?.title }}</p>
    <p>{{ Products_by_pk?.price }}</p>
  </div>
</template>

<script>
import gql from 'graphql-tag'
export default {
  apollo: {
    Products_by_pk: {
      query: gql`
      query product($id: Int!) {
        Products_by_pk(id: $id){
          id
          title
          description
          price
          Images{
            imageURL
          }
        }
      }`,
      variables() {
        return {
          id: this.$route.params.id,
        };
      },
    }
  }
}
</script>

<style scoped>
img{width: 450px;}
</style>