<template>
  <div class="container mx-auto mt-10">
    <Header />
    <div class="mt-12 md:flex">
      <Formulario 
        v-model:nombre="paciente.nombre"
        v-model:propietario="paciente.propietario"
        v-model:email="paciente.email"
        v-model:alta="paciente.alta"
        v-model:sintomas="paciente.sintomas"
        @guardar-paciente="guardarPaciente"
      />
      <div class="md:w-1/2 md:h-screen overflow-y-scroll">
        <h3 class="font-black text-3xl text-center">Administra tus Pacientes</h3>

        <div v-if="pacientes.length > 0">
          <p class="text-lg mt-5 text-center mb-10">Informacón de
            <span class="text-indigo-600 font-bold">Pacientes</span>
          </p>

          <Paciente 
            v-for="paciente in pacientes"
            :paciente="paciente"
          />

        </div>
        <p class="mt-20 text-2xl text-center" v-else>No hay pacientes</p> 
      </div>
    </div>
  </div>
</template>

<script setup>
  import { ref, reactive } from 'vue';
  import { uid } from 'uid' // Se descarga un paquete de ID desde npm
  import Header from './components/Header.vue';
  import Formulario from './components/Formulario.vue';
  import Paciente from './components/Paciente.vue';

  const pacientes = ref([])

  const paciente = reactive({
    id: null,
    nombre: '',
    propietario: '',
    email: '',
    alta: '',
    sintomas: ''
  })

  const guardarPaciente = () => {
    pacientes.value.push({
      ...paciente,
      id: uid()
    })

    // Reiniciar pacientes

    paciente.nombre = ''
    paciente.propietario = ''
    paciente.email = ''
    paciente.alta = ''
    paciente.sintomas = ''

  }

</script>