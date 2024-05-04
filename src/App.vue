<script setup>
  import {reactive,ref,onMounted} from 'vue';
  import {db} from './data/productos'
  import Producto from './components/ProductoV.vue';
  import Header from './components/HeaderV.vue';

  // const state = reactive({
  //   productos : db, 
  // });

  const productos = ref([]);
  const carrito = ref([]);
  //console.log(productos.value);
  
  onMounted(() =>{
    productos.value = db; // Esto nos sirve para actualizar la vista con los productos
  });


const agregarCarrito = (producto) =>{ 
   const existeCarrito = carrito.value.findIndex(prod => prod.id === producto.id);
   if(existeCarrito >= 0){
      const producto = carrito.value[existeCarrito];
      producto.cantidad++;
      return;
   }else{
      producto.cantidad = 1; 
      carrito.value.push(producto);
   }
}


const incrementarCantidad =  (id) => {
   const index = carrito.value.findIndex((prod) => prod.id === id);
   if(carrito.value[index].cantidad >= 5) return;
   carrito.value[index].cantidad++;
}


const decrementarCantidad =  (id) => {
   const index = carrito.value.findIndex((prod) => prod.id === id);
   if(carrito.value[index].cantidad <= 1) return;
   carrito.value[index].cantidad--;
}

const eliminarProducto = (id) =>{
   carrito.value = carrito.value.filter(prod => prod.id !== id);
}

const vaciarCarrito = () =>{
   carrito.value = [];
}



</script>


<template>
   <div>
      <div class="container">

         <Header 
            :carrito="carrito"
            @incrementar-cantidad="incrementarCantidad"
            @decrementar-cantidad="decrementarCantidad"
            @eliminar-producto="eliminarProducto"
            @vaciar-carrito="vaciarCarrito"
         />

         <div id="lista-productos" class="container">
         <h1 class="titulo">Tienda de productos</h1>
         
         <div class="row">
            <Producto 
               v-for="producto in productos"
               :producto="producto"
               @agregar-carrito="agregarCarrito"
            />

         </div>
         </div>
         
      </div>
   </div>
</template>