<script setup>
import { ref } from "vue";
const sueldoActual = ref();
const porcentajeAumento = ref();
const nuevoSueldo = ref(0);
const calcularNuevoSueldo = () => {
  if (sueldoActual.value != undefined && porcentajeAumento.value != undefined) {
    sueldoActual.value = parseFloat(sueldoActual.value);
    porcentajeAumento.value = parseFloat(porcentajeAumento.value);
    nuevoSueldo.value = (
      sueldoActual.value +
      sueldoActual.value * (porcentajeAumento.value / 100)
    ).toFixed(2);
  }
};
</script>
<template>
  <div
    class="tab-pane fade show active"
    id="v-tabs-home"
    role="tabpanel"
    aria-labelledby="v-tabs-home-tab"
  >
    <div class="row g-3 formulario form-control">
      <div class="col-12">
        <label for="inputAddress" class="form-label">Sueldo Actual</label>
        <div class="input-group">
          <div class="input-group-text">
            <label class="form-label-icon">$</label>
          </div>
          <input
            required
            type="text"
            id="typeNumber"
            class="form-control form-input"
            v-model="sueldoActual"
          />
        </div>
      </div>
      <div class="col-12">
        <label for="inputAddress" class="form-label"
          >Porcentaje de Aumento</label
        >
        <div class="input-group">
          <div class="input-group-text">
            <label class="form-label-icon">%</label>
          </div>
          <input
            type="text"
            id="typeNumber"
            class="form-control form-input"
            min="0"
            max="100"
            v-model="porcentajeAumento"
            required
          />
        </div>
      </div>
      <div class="alert alert-success" role="alert">
        TIP 💡: Usar punto para decimales : 0.0175 o 0.11
      </div>
      <div class="col-12 d-grid">
        <button
          @click="calcularNuevoSueldo()"
          class="btn btn-success mb-3 btn-rounded"
        >
          <span>Calcular</span>
        </button>
      </div>
      <div v-if="nuevoSueldo != 0" class="alert alert-success" role="alert">
        Tu nuevo sueldo será de
        <a class="alert-link nuevoSueldo">{{ nuevoSueldo }} $</a>
      </div>
    </div>
  </div>
</template>
<style scoped>
.formulario {
  margin: 1rem;
}
.nuevoSueldo {
  font-size: x-large;
}
button span {
  font-size: 15px;
}
.formulario {
  background-color: #414141;
  color: #f0f0f0;
  border: none;
}
.form-label {
  color: #f0f0f0;
}
.form-label-icon {
  color: #229e33;
  border-color: #5e5e5e;
}
.form-input {
  background-color: #5e5e5e;
  color: #f0f0f0;
  border: none;
  font-size: 20px;
}
.input-group-text {
  border-color: #5e5e5e;
}
</style>
