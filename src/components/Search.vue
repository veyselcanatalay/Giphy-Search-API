<template>
<input placeholder="Type something for search" v-model="keyword" @input="onInput">
  
</template>

<script>

export default {
  name: 'Search',
  data(){
      return{
          keyword: '',
          timeout: null,
      }
  },
  
  methods: {
      onInput() {
          clearTimeout(this.timeout);
          this.timeout = setTimeout(() => {
              this.search()
          })
      },
      search(){
          fetch(`https://api.giphy.com/v1/gifs/search?api_key=pheN03mkzNPjHSu5TcAJIDizHSc89WUr&q=${this.keyword}&limit=25`)
          .then(response => response.json())
          .then(result => {
              console.log(result);
              this.$emit('fetch-gifs', result.data)
          })
      }
  }
}

//pheN03mkzNPjHSu5TcAJIDizHSc89WUr
</script>

<style scopped>
    input {
        padding: 10px 16px;
        border-radius: 4px;
        font-size: 18px;
        outline: 0;
        border: 2px solid #5f5f5f;
        display: block;
        width: 100%;
    }

    input:focus{
        border-color: #0078e0;
    }
</style>
