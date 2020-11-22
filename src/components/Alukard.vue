<template>
  <div>
    <h3>
      {{ alukardNumber }}
    </h3>
    <div>
      Count: {{ times.count }}
    </div>
    <div>
      Biggest number: {{ times.biggestNumber }}
    </div>
    <div>
      Lowest number: {{ times.lowestNumber }}
    </div>
    <div>
      Previous number: {{ times.previousNumber }}
    </div>
    <div>
      <ul>
        <li
          v-for="(i, k) in values"
          :key="k"
        >
          {{ i | listFilter(k) }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    alukardNumber: 0,
    times: {
      count: 0,
      biggestNumber: 0,
      lowestNumber: 0,
      previousNumber: 0
    },
    values: []
  }),

  filters: {
    listFilter(value, index) {
      return value * index
    }
  },

  created() {
    setInterval(() => {
      this.generateNum()
    }, 2000)
  },

  methods: {
    generateNum() {
      this.alukardNumber = Math.floor(Math.random() * 1001)
    }
  },

  watch: {
    alukardNumber(newValue, oldValue) {
      if(newValue === oldValue) return false

      this.times.count += 1

      this.values.push(newValue)

      if(newValue > this.times.biggestNumber) {
        this.times.biggestNumber = newValue
      }
    
      if(newValue < this.times.lowestNumber || this.times.lowestNumber === 0) {
        this.times.lowestNumber = newValue
      }
      
      if(oldValue) {
        this.times.previousNumber = oldValue
      }
    },

    times: {
      deep: true,
      immediate: true,
      handler: () => {
        console.log('Аналитика аналитикнулась')
      }
    }
  }
}
</script>
