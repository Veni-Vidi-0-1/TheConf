<template>
  <div class="
    block

    px-10
    py-5

    text-black
    hover:text-white

    rounded-md

    hover:shadow.md

    hover:bg-purple-400

    transition
    easy-in-out
    duration-100
  ">
    <label
      v-text="`${label}:`"
      class="
        m-2
      "
    />
    <input
      type="text"
      :value="value"
      :class="[...classes]"
      :placeholder="placeholder"
      @input="onInput"
    />
    
    <RaButton
      type="submit"
      @mouseover="testCallBack"
    >
      Button
    </RaButton>
  </div>
</template>

<script>
import RaButton from '@/components/elements/RaButton.vue'

let classes = [
  'px-4',
  'py-3',

  'leading-5',

  'border',

  'rounded-md',

  'text-black',

  'focus:outline-none',
  'focus:ring',
  'focus:border-blue-400',

  'transition',
  'easy-in-out',
  'duration-500',
  'animate-bounce',
]

export default {
  components: {
    RaButton
  },
  
  props: {
    status: {
      type: String,
      required: true
    },

    value: {
      type: [String, Number, Object],
      required: true
    },

    label: {
      type: [String, Number],
      default: () => 'Label'
    },

    placeholder: {
      type: [String, Number],
      default: () => 'Placeholder'
    }
  },

  methods: {
    onInput(e) {
      this.$emit('input', e.target.value)
    },

    testCallBack() {
      console.log('Im event')
    }
  },

  computed: {
    classes() {
      let res = classes

      if (this.status === 'success') {
        res.push('border-green-400')
      }

      if (this.status === 'danger') {
        res.push('border-red-400')
      }

      if (this.status === 'warning') {
        res.push('border-yellow-400')
      }

      return res
    }
  }
}
</script>