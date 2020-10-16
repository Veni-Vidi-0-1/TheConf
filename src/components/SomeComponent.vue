<template>
  <div :class="{'ra-red': isRed}">
    <p v-if="isRed">
      Winner name:{{ winnerName}}
    </p>

    <Evan
      v-else
      :num="number"
      @makeRed="makeRedHere"
    />
  </div>
</template>

<script>
// date-fns
import Evan from '@/components/Evan.vue'

export default {
  components: {
    Evan
  },

  data: () => ({
    number: 321,

    isRed: false,
    winnerName: ''
  }),

  mounted() {
    this.number = 666
  },

  methods: {
    makeRedHere(name) {
      this.isRed = true
      this.winnerName = name
    }
  }

}

</script>

<style lang="scss" scoped>  
  .ra-red {
    background-color: red;
    color: white;
    height: 500px;
    width: 500px;
    font-size: 30px;
  }
</style>
