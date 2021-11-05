<template>
  <div class="row">
    <div class="col-md-8">
      <div class="row">
        <div
          class="col-md-8 content-products"
          v-for="producto in productos"
          :key="producto.id"
        >
          <productoComponent
            :producto="producto"
            :estaEnCarrito="estaEnCarrito(producto)"
            @addProducto="sendProduct"
          ></productoComponent>
        </div>
      </div>
    </div>
    <div class="col-md-5 my-5">
      <carritoComponent
        :listcar="listaProductos"
        @deleteProducto="deleteProduct"
        @pagarProduct="pagarToltal"
      ></carritoComponent>
    </div>
  </div>
</template>

<script>
import productoComponent from "./components/productoComponent";
import carritoComponent from "./components/carritoComponent";
import productos from "./productos";
export default {
  name: "App",
  components: {
    productoComponent,
    carritoComponent,
  },
  data() {
    return {
      productos,
      listaProductos: [],
    };
  },
  methods: {
    sendProduct(value) {
      this.listaProductos.push(value);
      // console.log(value.titulo)
    },
    deleteProduct(value) {
      this.listaProductos = this.listaProductos.filter(
        (item) => item.id != value.id
      );
    },
    estaEnCarrito(producto) {
      const item = this.listaProductos.find((item) => item.id === producto.id);
      if (item) {
        return true;
      }
      return false;
    },
    pagarToltal() {
      alert("Gracias por su compra");
      this.listaProductos = [];
    },
  },
};
</script>

<style>
.content-products {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
