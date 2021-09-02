<template>
    <div class="gif" :style="`background-image: url(${gif.images.original.url})`"></div>  
</template>

<script>

export default {
  name: 'Gif',
  props: {
      gif: Object
  }
}
</script>

<style scopped>
    .gif{
        width: 240px;
        height: 240px;
        background-repeat: no-repeat;
        background-size: cover;
        background-position: center;
        margin-bottom: 20px;
        display: flex;
        justify-content: space-between;
    }
</style>
