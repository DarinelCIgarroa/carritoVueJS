<template>
  <div>
    <div class="card" style="width: 18rem">
      <img :src="producto.imagen" width="250" height="150" class="card-img-top" alt="#" />
      <div class="card-body">
        <h5 class="card-title">{{ producto.titulo }}</h5>
        <p class="card-text">
          Producto a precio rebajado
        </p>
        <p text-muted>{{ producto.precio }}</p>
        <button class="btn btn-primary form-control" @click.prevent="addcarrito(producto)" :disabled="estaEnCarrito">Agregar al carrito</button>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  name: "productoComponent",
  props:{
    producto: Object,
    estaEnCarrito: Boolean
  },
  methods:{
    addcarrito(value){
      this.$emit('addProducto', value)
    }
  }
};
</script>

<style scoped>
  .card{
    margin: 10px !important;
  }
</style>