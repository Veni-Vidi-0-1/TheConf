<template>
  <div class="container p-24 m-24">
    <RaInput
      v-model="value"
      label="Test label"
      status="danger"
      placeholder="Input placeholder"
    />
    <RaInput
      v-model="value"
      label="Test label"
      status="warning"
      placeholder="Input placeholder"
    />
    <RaInput
      v-model="value"
      label="Test label"
      status="success"
      placeholder="Input placeholder"
    />
  </div>
</template>

<script>
import RaInput from '@/components/elements/RaInput.vue'

export default {
  components: {
    RaInput
  },

  data: () => ({
    value: ''
  })
}
</script>
