

  <template>
    <div class="container-fluid">
      <div class="row justify-content-center">
        <div class="col-md-6 col-lg-12 bg-light p-4 rounded shadow">
          <h4 class="text-center mb-4 text-primary">Registrar Consulta</h4>
          <form @submit.prevent="agregarCita">
            <div class="form-group mb-3">
              <label for="paciente" class="form-label">Paciente</label>
              <input
                type="text"
                id="paciente"
                v-model="paciente"
                class="form-control"
                placeholder="Nombre del paciente"
                required
              />
            </div>
  
            <div class="form-group mb-3">
              <label for="fecha" class="form-label">Fecha</label>
              <input
                type="date"
                id="fecha"
                v-model="fecha"
                class="form-control text-center"
                required
              />
            </div>
  
            <div class="form-group mb-3">
              <label for="hora" class="form-label">Hora</label>
              <input
                type="time"
                id="hora"
                v-model="hora"
                class="form-control text-center"
                required
              />
            </div>
  
            <div class="form-group mb-3">
              <label for="gravedad" class="form-label">Gravedad</label>
              <select
                id="gravedad"
                v-model="gravedad"
                class="form-select"
                required
              >
                <option value="">Seleccione</option>
                <option value="Grave">Alta</option>
                <option value="Moderada">Media</option>
                <option value="Leve">Baja</option>
              </select>
            </div>
  
            <div class="form-group mb-3">
              <label for="motivo" class="form-label">Motivo</label>
              <input
                type="text"
                id="motivo"
                v-model="motivo"
                class="form-control"
                placeholder="Motivo de la consulta"
                required
              />
            </div>
  
            <div class="text-center">
              <button
                type="submit"
                class="btn btn-primary w-100"
                :disabled="paciente.length === 0 || fecha.length === 0 || hora.length === 0 || gravedad.length === 0 || motivo.length === 0"
              >
                Agregar
              </button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        paciente: '',
        fecha: '',
        hora: '',
        gravedad: '',
        motivo: ''
      };
    },
    methods: {
      agregarCita() {
        if (this.paciente && this.fecha && this.hora && this.gravedad && this.motivo) {
          this.$emit('nueva-cita', {
            paciente: this.paciente,
            fecha: this.fecha,
            hora: this.hora,
            gravedad: this.gravedad,
            motivo: this.motivo
          });

          this.paciente = '';
          this.fecha = '';
          this.hora = '';
          this.gravedad = '';
          this.motivo = '';
        } else {
          alert("Por favor, complete todos los campos.");
        }
      }
    }
  };
  </script>
  
<style scoped>

.bg-light {
  background-color: rgba(255, 255, 255, 0.8) !important;
}

.shadow {
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}
</style>