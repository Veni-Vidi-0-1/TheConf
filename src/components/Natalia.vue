<template>
  <div>
    <input v-model="value">
    {{ value }}
    123
    <img
      v-for="(cat, key) in cats"
      v-swipe
      :key="key"
      :src="cat"
      width="500"
    >
  </div>
</template>

<script>
  export default {
    props: {
      cats: {
        type: Array | Object,        
        required: true
      }
    },

    data: () => ({
      value: ''
    })
  }
  


  

  
</script>
