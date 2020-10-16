<template>
  <div
    class="ra-user-select"
    @click="onChange()"
  >
    <div v-if="isFlag">
      Evan component: {{ num }}
    </div>
    <div v-else>
      Dz component: {{ dz }}
    </div>
    <div v-if="stat.evan >= 0 && stat.dz >= 0">
      <p>Statistic views:</p>
      <p>Evan clicks: {{ stat.evan }}</p>
      <p>Dz clicks: {{ stat.dz }}</p>
    </div>
    <div v-else>
      <p>Sorry no statistic</p>
    </div>

    <br />

    <div>
      {{ testMethod() }}
      <br />
      {{ testComputed }}
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      num: {
        type: Number | String,
        required: true,
        default: () => 300
      }
    },

    data: () => ({
      dz: 23,
      isFlag: true,

      stat: {
        evan: 0,
        dz: 0
      }
    }),

    methods: {
      onChange() {
        this.isFlag = !this.isFlag
        
        if (this.isFlag) {
          this.stat.evan += 1
          if (this.stat.evan >= 20) {
            this.$emit('makeRed', 'Evan')
          }
        } else {
          this.stat.dz += 1
          if (this.stat.dz >= 20) {
            this.$emit('makeRed', 'Dzzz')
          }
        }
      },

      testMethod() {
        return this.isFlag
      }
    },

    computed: {
      testComputed() {
        return this.isFlag
      }
    },

    watch: {
      stat: {
        deep: true,
        immediate: true,

        handler: function(newValue, oldValue) {
          console.log('NEW STAT VALUE', newValue)
        }
      }
    }
  }

  /*
  stat: {
    evan: 5,
    dz: 3
  }

  stat.evan = 5

  stat

  stat.evan
  stat.dz


  */
</script>

<style>
  .ra-user-select {
    user-select: none;
  }
</style>