<template>
  <button
    v-on="$listeners"
    :attrs="[...$attrs]"
    :class="[...classes]"
  >
    <slot />
  </button>
</template>
<script>
  let classes = [
    'px-4',
    'py-2',
    'm-2',

    'text-black',
    'outline-none',
    'focus:outline-none',

    'rounded-md',
    'shadow-md',

    'border',
    'border-4',
    'border-gray-400',

    'bg-gray-100',

    'ring',
    'ring-yellow-500',
    'ring-opacity-50',
    'hover:ring-opacity-100',

    'animate-spin',
  ]
  
  export default {
    computed: {
      classes() {
        return classes
      }
    }
  }
</script>
