<template>
  <div class="ra-images">
    <img  
      v-for="(img, key) in imgArray"
      v-filter:lenni.fee.bee
      v-rotate="90"
      :key="key"
      :src="img"
      @click="$refs.audio.volume = 0.1; $refs.audio.play()"
    />

    <audio
      ref="audio"
      :src="audioUrl"
    />
  </div>
</template>

<script>
let imgArray = [
  'https://o-prirode.ru/wp-content/uploads/2018/03/delfin-e1519921979189.jpg',
  'https://i.ytimg.com/vi/7QlYKdcwglE/maxresdefault.jpg',
  'https://s1.stc.all.kpcdn.net/putevoditel/projectid_103889/images/tild3630-6532-4530-a136-383266363334__dolphins-906175_1280.jpg',
  'https://ichef.bbci.co.uk/news/640/amz/worldservice/live/assets/images/2015/02/18/150218144801_dolphines_happy_624x351_thinkstock.jpg',
  'https://moya-planeta.ru/upload/images/xl/65/1b/651ba2867b73fd8366c84b47d73632a8.jpg',
  'https://naukatehnika.com/files/journal/nauka/biologia_i_medicina/18.12.18-delfinyi%E2%80%93pridirchivyi/image_1.jpg',
  'https://upload.wikimedia.org/wikipedia/commons/b/b0/Parc_Asterix_20.jpg',
  'https://bigpicture.ru/wp-content/uploads/2016/07/dolphins15.jpg',
  'https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcR4XJgJyBnhGeGrxw50T7JTI2oFG-fi4nENZw&usqp=CAU',
  'https://i2.wp.com/paikea.ru/wp-content/uploads/2012/04/IMG_042438.jpg?fit=640%2C384'
]

export default {
  data: () => ({
    name: 'VOLOLO',

    audioUrl: 'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3'
  }),

  directives: {
    filter: {
      inserted(el, binding, vnode) {
        // vnode.context.name === this.
        setTimeout(() => {
          el.style.filter = 'hue-rotate(90deg)'
        }, 1500)
      },

      unbind(el, binding, vnode) {}
    },

    rotate: {
      inserted(el, binding, vnode) {
        let deg = 0
        let isPlus = true

        let interval = setInterval(() => {
          if (isPlus) deg += 90
          else deg -= 90

          el.style.transform = `rotate(${deg}deg)`
          el.style.transition = 'all 1s ease-out'
        }, 150)

        el.onclick = () => {
          isPlus = !isPlus
        }

        el.ondblclick = () => {
          clearInterval(interval)
        }
      }

    }

  },

  computed: {
    imgArray() {
      return imgArray
    }
  }
}
</script>

<style lang="scss" scoped>
  .dt-image {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    flex-wrap: wrap;
    img {
      flex: 0 0 32%;
    }
  }

  .ra-images {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    place-items: center;
    gap: 20px;

    img {
      max-width: 300px;
    }
  }
</style>


