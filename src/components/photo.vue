<template>
  <div class='col-12 col-sm-6 col-lg-3 form-group'>
    <img @click="toggleImage(true)" class="base" :src="imagePath(url)">
  
    <transition name='fade'>
      <div v-if="openedImage" class='overlay'>
        <img @click="toggleImage(false)" v-if="openedImage" class="big" :src="imagePath(url)">
      </div>
    </transition>
  </div>
</template>

<script>
  export default {
    props: ['url'],
    data() {
      return {
        openedImage: false
      }
    },
    methods: {
      imagePath(url) {
        return require('../assets/' + url + '.jpg')
      },
      toggleImage(value) {
        this.openedImage = value
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
  .base {
    opacity: 1;
    max-width: 100%;
    height: auto;
    border: 5px solid white;
    border-radius: 10px;
    transition: all 1s;
    cursor: pointer;
    margin-bottom: 1rem
  }
  
  .base:hover {
    opacity: 0.2;
    transform: scale(1.1);
  }
  
  .big {
    border: 5px solid white;
    border-radius: 10px;
    position: fixed;
    max-height: 90%;
    max-width: 90%;
    width: auto;
    margin: auto;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    z-index: 1000;
    cursor: pointer;
  }
  
  .overlay {
    left: 0;
    top: 0;
    z-index: 900;
    width: 100%;
    height: 100%;
    position: fixed;
    background-color: black;
    background: rgba(0, 0, 0, 0.6);
  }
</style>
