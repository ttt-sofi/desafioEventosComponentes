

<template>
    <div class="container mt-5">
      <div class="row">

        <div class="col-lg-6">
          <FormularioCita @nueva-cita="agregarCita" />
        </div>
        <div class="col-lg-6">
          <div v-if="citas.length === 0" class="alert alert-warning text-center">
            Aún no hay consultas registradas
          </div>
          
          <div v-else>
            <h4 class="text-center mb-4 text-primary">Consultas Registradas</h4>
            <table class="table table-bordered table-hover">
              <thead class="thead-light">
                <tr>
                  <th>Paciente</th>
                  <th>Fecha</th>
                  <th>Hora</th>
                  <th>Gravedad</th>
                  <th>Motivo</th>
                  <th>Acciones</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="(cita, index) in citas" :key="index" :class="getRowClass(cita.gravedad)">
                  <td>{{ cita.paciente }}</td>
                  <td>{{ cita.fecha }}</td>
                  <td>{{ cita.hora }}</td>
                  <td>{{ cita.gravedad }}</td>
                  <td>{{ cita.motivo }}</td>
                  <td>
                    <button class="btn btn-danger btn-sm" @click="eliminarCita(index)">
                      Eliminar
                    </button>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import FormularioCita from './FormularioCita.vue';
  
  export default {
    components: {
      FormularioCita
    },
    data() {
      return {
        citas: []
      };
    },
    methods: {
      agregarCita(nuevaCita) {
        this.citas.push(nuevaCita);
      },
      eliminarCita(index) {
        this.citas.splice(index, 1);
      },
      getRowClass(gravedad) {
        switch (gravedad) {
          case 'Grave':
            return 'table-danger';
          case 'Moderada':
            return 'table-warning';
          case 'Leve':
            return 'table-success';
          default:
            return '';
        }
      }
    }
  };
  </script>
  
  <style scoped>
    .table {
      margin-top: 20px;
    }
  </style>
  