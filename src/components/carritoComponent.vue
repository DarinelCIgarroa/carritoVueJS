<template>
  <div>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">Producto</th>
          <th scope="col">Precio</th>
          <th scope="col">Imagen</th>
          <th scope="col">Eliminar</th>
        </tr>
      </thead>
      <tbody v-for="item in listcar" :key="item">
        <tr>
          <td>{{ item.titulo }}</td>
          <td>${{ item.precio }}</td>
          <td><img :src="item.imagen" width="60" height="60" /></td>
          <td><button class="btn btn-danger" @click="productDelete(item)">Eliminar</button></td>
        </tr>
      </tbody>
      <tfoot>
        <td>Total: $ {{ total }}</td>
      </tfoot>
    </table>
    
    <button v-if="listcar.length != 0" :disabled="listcar.length === 0" class="btn btn-success" @click="pagar">Pagar</button>
  </div>
</template>

<script>
export default {
  name: "carritoComponent",
  props: {
    listcar: Object,
  },
  computed:{
    total(){
     return this.listcar.reduce((contador, item) => contador + Number(item.precio),0);
    }
  },
  methods:{
    productDelete(value){
       this.$emit('deleteProducto', value)
    },
    pagar(){
      this.$emit('pagarProduct')
    }
  }
};
</script>
