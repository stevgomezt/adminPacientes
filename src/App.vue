<template>
    <div class="container mx-auto mt-20"></div>
    <Header />
    <div class="mt-12 md:flex">
        <Formulario
            v-model:mascota="paciente.mascota"
            v-model:propietario="paciente.propietario"
            v-model:email="paciente.email"
            v-model:alta="paciente.alta"
            v-model:sintomas="paciente.sintomas"
            @guardar-paciente="guardarPaciente"
        />
        <div class="md:w-1/2 md:h-screen overflow-y-scroll">
            <h3 class="font-black text-3xl text-center">
                Administra tus Pacientes
            </h3>
            <div v-if="pacientes.length > 0"></div>
            <p v-else class="mt-10 text-2xl text-center">No hay Pacientes</p>
        </div>
    </div>
</template>

<script setup>
import { ref, reactive } from "vue";
import Header from "./components/Header.vue";
import Formulario from "./components/Formulario.vue";

const pacientes = ref([]);

const paciente = reactive({
    mascota: "",
    propietario: "",
    email: "",
    alta: "",
    sintomas: "",
});

const guardarPaciente = () => {
    console.log("agregando...");
    pacientes.value.push(paciente);
};
</script>

<style lang="scss" scoped></style>
