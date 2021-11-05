<template>
  <h2>Tipo de Cuenta: {{ cuenta }}</h2>
  <h2>Saldo: {{ saldo }}</h2>
  <h2>{{ estado ? "Cuenta Activa" : "Cuenta Inactiva" }}</h2>
  <div v-for="(item, index) in servicios" :key="index">
    {{ index + 1 }}. {{ item }}
  </div>
  <AccionSaldo texto="Aumentar Saldo" @accion="aumentar" />
  <AccionSaldo
    texto="Disminuir Saldo"
    @accion="disminuir"
    :desactivar="desactivar"
  />
</template>

<script>
import AccionSaldo from "./AccionSaldo";

export default {
  components: {
    AccionSaldo,
  },
  data() {
    return {
      saldo: 1000,
      cuenta: "Ahorros",
      estado: true,
      servicios: ["Retiros", "Consignaciones", "Prestamos", "Giros"],
      desactivar: false,
    };
  },
  methods: {
    aumentar() {
      this.saldo = this.saldo + 100;
      this.desactivar = false;
    },
    disminuir() {
      if (this.saldo === 0) {
        this.desactivar = true;
        alert("sin saldo");
        return;
      }
      this.saldo = this.saldo - 100;
    },
  },
};
</script>

<style></style>
