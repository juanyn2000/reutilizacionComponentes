<template>
  <section class="contentForm">
    <div class="form">
      <div>
        <label :style="{ color: paciente ? 'black' : 'red' }">Paciente</label>
        <input type="text" v-model="paciente" />
      </div>
      <div>
        <label :style="{ color: fecha ? 'black' : 'red' }">Fecha</label>
        <input type="date" v-model="fecha" />
      </div>
      <div>
        <label :style="{ color: hora ? 'black' : 'red' }">Hora</label>
        <input type="time" v-model="hora" />
      </div>
      <div>
        <label :style="{ color: gravedad ? 'black' : 'red' }">Gravedad</label>
        <select v-model="gravedad">
          <option value="">Seleccione</option>
          <option value="green">Baja</option>
          <option value="yellow">Media</option>
          <option value="red">Alta</option>
        </select>
      </div>
      <div>
        <label :style="{ color: motivo ? 'black' : 'red' }">Motivo</label>
        <input type="text" v-model="motivo" />
      </div>
    </div>
    <button @click="agregarCita" v-if="paciente=='' || fecha=='' || hora=='' || gravedad=='' || motivo == ''" disabled>Agregar</button>
    <button @click="agregarCita" v-else>Agregar</button>
  </section>
  <section class="cita">
    <div v-for="(cita, index) in citas" :key="cita">
      <Cita
        :paciente="cita.paciente"
        :fecha="cita.fecha"
        :hora="cita.hora"
        :gravedad="cita.gravedad"
        :motivo="cita.motivo"
        @eliminarCita="citas.splice(index, 1)"
      />
    </div>
  </section>
</template>

<script>
import Cita from "./Cita.vue";
export default {
  name: "Formulario",
  components: {
    Cita,
  },
  data() {
    return {
      paciente: "",
      fecha: "",
      hora: "",
      gravedad: "",
      motivo: "",
      citas: [],
    };
  },
  methods: {
    agregarCita() {
      if (
        this.paciente &&
        this.fecha &&
        this.hora &&
        this.gravedad &&
        this.motivo
      ) {
        this.citas.push({
          paciente: this.paciente,
          fecha: this.fecha,
          hora: this.hora,
          gravedad: this.gravedad,
          motivo: this.motivo,
        });
      }
    },
  },
};
</script>

<style scoped>
.contentForm {
  margin: 2rem auto;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  justify-content: center;
  border: 1px solid #000;
  padding: 1rem;
  width: max-content;
}
.form {
  margin: auto;
  display: flex;
  gap: 1rem;
  justify-content: center;
}
label {
  display: block;
  margin-bottom: 0.5rem;
}
button {
  margin-inline: auto;
  padding: 0.5rem 1rem;
  cursor: pointer;
  width: max-content;
}
.cita {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin: auto;
}
</style>
