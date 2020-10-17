<template>
  <div>
    <Natalia 
      :cats="cats"
    />
  </div>
</template>

<script>
import Natalia from '@/components/Natalia.vue'

const cats = [
  'https://i.pinimg.com/originals/f4/d2/96/f4d2961b652880be432fb9580891ed62.png',
  'https://ichef.bbci.co.uk/news/640/cpsprodpb/14236/production/_104368428_gettyimages-543560762.jpg',
  'https://telegra.ph/file/a23d68b6ee75f6fe6fa67.jpg',
  'https://i.ytimg.com/vi/R28lU1Ua8J0/maxresdefault.jpg',
  'https://kaifolog.ru/uploads/posts/2020-06/1592383368_002.jpg',
  'https://image.winudf.com/v2/image/Y29tLkhEV2FsbHBhcGVyLmN1dGVjYXRjX3NjcmVlbl8wXzE1MjQzNzk3MDBfMDgw/screen-0.jpg?fakeurl=1&type=.jpg',
  'https://64.media.tumblr.com/036c3491ca544f1893a284b5ac746fd7/tumblr_pvxkrjVzhA1xb21v7o2_500.jpg',
  'https://www.google.com/url?sa=i&url=https%3A%2F%2Fsocial.techjunkie.com%2Fcat-memes%2F&psig=AOvVaw2omIGJuEnD5LuOZtpMwhsa&ust=1603041710804000&source=images&cd=vfe&ved=2ahUKEwjM45DvkbzsAhXHyioKHfkUAYUQjRx6BAgAEAc',
]

export default {
  components: {
    Natalia
  },
  
  data: () => ({
    cats: []
  }),
  
  mounted() {
    this.someFunction()

    setInterval(() => {
      this.someFunction()
    }, 1500)
  },

  methods:{
    someFunction() {
      this.cats  = cats.sort(() => Math.random() - 0.5);
    }
  }
}
</script>

<style lang="scss" scoped>
</style>

/*
  парковочное место под курсоры
  парковочное место под курсоры
  парковочное место под курсоры
  парковочное место под курсоры
  парковочное место под курсоры
*/