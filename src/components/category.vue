<template>
  <div class='row'>
    <photo v-for="photo in photos" :url="photo" :key="photo">
    </photo>
  </div>
</template>

<script>
  import photo from '../components/photo'
  
  export default {
    props: ['photos'],
    name: 'Category',
    components: {
      photo
    }
  
  }
</script>

<style>
  .fade-enter-active,
  .fade-leave-active {
    transition: opacity 1s;
  }
  
  .fade-enter,
  .fade-leave-to {
    opacity: 0;
  }
</style>
