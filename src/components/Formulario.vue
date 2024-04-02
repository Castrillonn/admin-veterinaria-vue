<template>  
  <div class="md:w-1/2">
    <h2 class="font-black text-3xl text-center">Seguimiento Mascotas</h2>
    <p class="text-lg mt-5 text-center mb-10">Añade Mascotas y
      <span class="text-indigo-600 font-bold">Adminístralas</span>
    </p>
    <Alerta
      v-if="alerta.mensaje"
      v-bind:alerta="alerta"
    />
    <form
      class="bg-white shadow-md rounded-lg py-10 px-5 mb-10"
      v-on:submit.prevent="validar"
    >
      <div class="mb-5">
        <label
          for="mascota"
          class="block text-gray-700 uppercase font-bold">
          Nombre Mascota
        </label>
        <input
          id="mascota"
          type="text"
          placeholder="Nombre de la mascota"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          @input="$emit('update:nombre', $event.target.value)"
        >
      </div>
      <div class="mb-5">
        <label
          for="propietario"
          class="block text-gray-700 uppercase font-bold">
          Nombre Propietario
        </label>
        <input
          id="propietario"
          type="text"
          placeholder="Nombre del propietario"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
        >
      </div>

      <div class="mb-5">
        <label
          for="email"
          class="block text-gray-700 uppercase font-bold">
          Email
        </label>
        <input
          id="email"
          type="email"
          placeholder="email"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
        >
      </div>

      <div class="mb-5">
        <label
          for="alta"
          class="block text-gray-700 uppercase font-bold">
          Fecha de Alta
        </label>
        <input
          id="alta"
          type="date"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
        >
      </div>

      <div class="mb-5">
        <label
          for="sintomas"
          class="block text-gray-700 uppercase font-bold">
          Síntomas
        </label>
        <textarea
          id="sintomas"
          placeholder="Describe los síntomas"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md h-32"
        >
        </textarea>
      </div>

      <input
        type="submit"
        value="Registrar Paciente"
        class="bg-indigo-600 w-full p-3 text-white uppercase font-bold hover:bg-indigo-700 cursor-pointer transition-colors">
    </form>
  </div>
</template>

<script setup>

  import { reactive } from 'vue'
  import Alerta from './Alerta.vue'

  const alerta = reactive({
    tipo: '',
    mensaje: ''
  })

  defineEmits(['update:nombre'])

  const validar = () => {
    if (Object.values(paciente).includes('')) {
      alerta.mensaje = 'Guardado Correctamente'
      alerta.tipo = 'exito'
      return
    }
  }

</script>