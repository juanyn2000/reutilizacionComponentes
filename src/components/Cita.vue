<template>
    <div class="citaContenedor" :style="{backgroundColor:gravedad}">
        <h3>Paciente</h3>
        <p>{{paciente}}</p>
        <h3>Fecha</h3>
        <p>{{fecha}}</p>
        <h3>Hora</h3>
        <p>{{hora}}</p>
        <h3>Gravedad</h3>
        <p>{{gravedad}}</p>
        <h3>Motivo</h3>
        <p>{{motivo}}</p>
        <button @click="$emit('eliminarCita')">Eliminar</button>
    </div>
</template>

<script>
export default {
    name: 'Cita',
    props: ["paciente", "fecha", "hora", "gravedad", "motivo"]

};
</script>

<style scoped>
.citaContenedor {
    
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 10px;

    width: 300px;
}
button {
    margin-inline: auto;
    padding: 0.5rem 1rem;
    cursor: pointer;
    width: 150px;
    margin-bottom: 20px;
}
p, h3 {
    margin: auto;
    padding: 0;
}
</style>