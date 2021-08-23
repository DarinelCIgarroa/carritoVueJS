<template>
  
      <div class="row">
          <div class="col-md-7">
            <div class="row">
              <div class="col-md-6" v-for="producto in productos" :key="producto.id">
                <productoComponent :producto="producto"></productoComponent>
              </div>
            </div>
          </div>
      </div>
  
</template>

<script>
import productoComponent from './components/productoComponent'
import productos from './productos'
export default {
  name: 'App',
  components: {
    productoComponent
  },
  data(){
    return{
      productos
    }
  }
}
</script>

<style>

</style>
