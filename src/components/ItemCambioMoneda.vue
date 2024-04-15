<script setup>
import { ref } from "vue";

const operacion = ref();
const cantidad = ref();
const cantidadRequerida = ref();
const cambio = ref();
const totalCambiado = ref();
const totalRequerido = ref();
const checkCantidadEspecifica = ref(0);
const obtenerBandera = (operacion) => {
  if (operacion === "pebol") {
    return ["🇦🇷", "🇧🇴"];
  }
  if (operacion === "pedol") {
    return ["🇦🇷", "🇺🇸"];
  } else {
    return ["🇧🇴", "🇺🇸"];
  }
};

const obtenerTotalCambiado = () => {
  if (cambio.value != undefined) {
    cambio.value = parseFloat(cambio.value);
    cantidad.value = parseFloat(cantidad.value);
    if (operacion.value === "pebol") {
      totalCambiado.value = (cantidad.value * cambio.value).toFixed(2);
      totalRequerido.value = (cantidadRequerida.value / cambio.value).toFixed(
        2
      );
    } else {
      totalCambiado.value = (cantidad.value / cambio.value).toFixed(2);
      totalRequerido.value = (cantidadRequerida.value * cambio.value).toFixed(
        2
      );
    }
  }
};
</script>
<template>
  <div
    class="tab-pane fade"
    id="v-tabs-profile"
    role="tabpanel"
    aria-labelledby="v-tabs-profile-tab"
  >
    <div class="row g-3 formulario form-control">
      <label>Seleccione que monedas desea cambair</label>
      <div class="checks-group">
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="flexRadioDefault"
            id="flexRadioDefault1"
            v-model="operacion"
            value="pebol"
          />Pesos 🇦🇷 - Bolivianos 🇧🇴
        </div>
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="flexRadioDefault"
            id="flexRadioDefault2"
            value="pedol"
            v-model="operacion"
          />Pesos 🇦🇷 - Dolares 🇺🇸
        </div>
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="flexRadioDefault"
            id="flexRadioDefault3"
            value="boldol"
            v-model="operacion"
          />Bolivianos 🇧🇴 - Dolares 🇺🇸
        </div>
        <div class="alert alert-success mt-3" role="alert">
          TIP 💡: Usar punto para decimales : 0.0175 o 0.11
        </div>
      </div>
      <div v-if="operacion !== undefined">
        <div class="col-12">
          <label for="inputAddress" class="form-label"
            >Cambio {{ obtenerBandera(operacion)[1] }}</label
          >
          <div class="input-group">
            <div class="input-group-text">
              <label class="form-label-icon">$</label>
            </div>
            <input
              required
              type="text"
              id="typeNumber"
              class="form-control form-input"
              v-model="cambio"
              @input="quitarResultado"
            />
          </div>
        </div>
        <div class="col-12 mt-3">
          <div class="form-check">
            <input
              class="form-check-input"
              type="checkbox"
              value=""
              v-model="checkCantidadEspecifica"
            />
            <label class="form-check-label" for="flexRadioDefault1">
              Marque aqui si desea una cantidad especifica de
              {{ obtenerBandera(operacion)[1] }}
            </label>
          </div>
          <div v-if="checkCantidadEspecifica">
            <label class="form-label mt-3"
              >Cantidad de
              {{ obtenerBandera(operacion)[1] }}
              que desea</label
            >
            <div class="input-group">
              <div class="input-group-text">
                <label class="form-label-icon">$</label>
              </div>
              <input
                required
                type="text"
                id="typeNumber"
                class="form-control form-input"
                v-model="cantidadRequerida"
              />
            </div>
          </div>
        </div>
        <div class="col-12 mt-3" v-if="!checkCantidadEspecifica">
          <label for="inputAddress" class="form-label"
            >Cantidad de
            {{ obtenerBandera(operacion)[0] }}
            que quiere cambiar
          </label>
          <div class="input-group">
            <div class="input-group-text">
              <label class="form-label-icon">$</label>
            </div>
            <input
              type="text"
              id="typeNumber"
              class="form-control form-input"
              required
              v-model="cantidad"
            />
          </div>
        </div>
        <div class="col-12 mt-3 d-grid">
          <button
            @click="obtenerTotalCambiado()"
            class="btn btn-success mb-3 btn-rounded"
          >
            <span>Calcular</span>
          </button>
          <div
            v-if="totalCambiado != undefined"
            class="alert alert-success"
            role="alert"
          >
            <p v-if="!checkCantidadEspecifica">
              Obtendras:
              <a class="alert-link totalCambiado">{{ totalCambiado }} $</a>
            </p>
            <p v-if="checkCantidadEspecifica">
              Necesitas :
              <a class="alert-link totalCambiado">{{ totalRequerido }} $</a>
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.formulario {
  margin: 1rem;
}
.totalCambiado {
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
