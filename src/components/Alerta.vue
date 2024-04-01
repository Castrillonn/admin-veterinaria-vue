<template>
  <div
    :class="[alertaError ? 'bg-red-500' : 'bg-green-500']"
    class="text-white text-center p-3 uppercase font-bold mb-3 rounded-md">
    {{ alerta.mensaje }}
  </div>
</template>

<script setup>

  import { computed } from 'vue'

  const props = defineProps({
    alerta: {
      type: Object,
      required: true
    }
  })

  const alertaError = computed (() => {
    return props.alerta.tipo === 'error'
  })

</script>