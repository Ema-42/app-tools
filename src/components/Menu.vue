<script setup>
import ItemAumentoSueldo from "./ItemAumentoSueldo.vue";
import ItemCalcularQuincena from "./ItemCalcularQuincena.vue";
import ItemCambioMoneda from "./ItemCambioMoneda.vue";

</script>
<template>
  <div class="row w-100 menu-contenedor">
    <div class="col-4">
      <!-- Tab navs -->
      <div
        class="nav flex-column nav-tabs menu-items"
        id="v-tabs-tab"
        role="tablist"
        aria-orientation="vertical"
      >
        <a
          class="nav-link active"
          id="v-tabs-home-tab"
          data-mdb-toggle="tab"
          href="#v-tabs-home"
          role="tab"
          aria-controls="v-tabs-home"
          aria-selected="true"
          >Aumento de Sueldo
        </a>
        <a
          class="nav-link"
          id="v-tabs-profile-tab"
          data-mdb-toggle="tab"
          href="#v-tabs-profile"
          role="tab"
          aria-controls="v-tabs-profile"
          aria-selected="false"
          >Cambio de moneda</a
        >
        <a
          class="nav-link"
          id="v-tabs-messages-tab"
          data-mdb-toggle="tab"
          href="#v-tabs-messages"
          role="tab"
          aria-controls="v-tabs-messages"
          aria-selected="false"
          >Calcular Quincena
        </a>
      </div>
    </div>

    <div class="col-8">
      <div class="tab-content" id="v-tabs-tabContent">
        <ItemAumentoSueldo></ItemAumentoSueldo>
        <ItemCambioMoneda></ItemCambioMoneda>
        <ItemCalcularQuincena></ItemCalcularQuincena>
      </div>
    </div>
  </div>

</template>
<style scoped>
a.nav-link {
  font-size: 15px;
}
.menu-contenedor{
  background-color: #252525;
  color: aliceblue;
}
.nav-link{
  background-color: #252525;
  color: aliceblue;
}
.nav-link.active{
  background-color: #424242;
  color: aliceblue;
  border-color: #229e33;
  border-bottom-width: 3px;
}
.nav-link:hover{
  background-color: #424242;
}
</style>
