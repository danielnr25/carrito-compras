<script setup>
  import {reactive,ref,onMounted, watch} from 'vue';
  import {db} from './data/productos'
  import Producto from './components/ProductoV.vue';
  import Header from './components/HeaderV.vue';

  // const state = reactive({
  //   productos : db, 
  // });

  const productos = ref([]);
  const carrito = ref([]);
  const cantidadCarrito = ref(0);

  watch(carrito, ()=>{
      guardarLocalStorage();
  },{
   deep:true
  })


  onMounted(() =>{
    productos.value = db; // Esto nos sirve para actualizar la vista con los productos

   const carritoStorage = localStorage.getItem('carrito');
   
   if(carritoStorage){
      carrito.value = JSON.parse(carritoStorage);
   }

  });

  const guardarLocalStorage = () =>{
    localStorage.setItem('carrito',JSON.stringify(carrito.value));
  }


const agregarCarrito = (producto) =>{ 
   const existeCarrito = carrito.value.findIndex(prod => prod.id === producto.id);
   if(existeCarrito >= 0){
      const producto = carrito.value[existeCarrito];
      producto.cantidad++;
      cantidadCarrito.value++;
      return;
   }else{
      producto.cantidad = 1; 
      carrito.value.push(producto);
      cantidadCarrito.value++;
   }
   guardarLocalStorage();
   
}


const incrementarCantidad =  (id) => {
   const index = carrito.value.findIndex((prod) => prod.id === id);
   if(carrito.value[index].cantidad >= 5) return;
   carrito.value[index].cantidad++;
   cantidadCarrito.value++;
}


const decrementarCantidad =  (id) => {
   const index = carrito.value.findIndex((prod) => prod.id === id);
   if(carrito.value[index].cantidad <= 1) return;
   carrito.value[index].cantidad--;
   cantidadCarrito.value--;
}

const eliminarProducto = (id) =>{
   carrito.value = carrito.value.filter(prod => prod.id !== id);
   cantidadCarrito.value--;
}

const vaciarCarrito = () =>{
   carrito.value = [];
   cantidadCarrito.value = 0;
}

const pagarCompra = () =>{
   alert('Compra realizada con exito');
   vaciarCarrito();
   cantidadCarrito.value = 0;
}



</script>


<template>
   <div>
      <div class="container">

         <Header 
            :carrito="carrito"
            :cantidadCarrito="cantidadCarrito"
            @incrementar-cantidad="incrementarCantidad"
            @decrementar-cantidad="decrementarCantidad"
            @eliminar-producto="eliminarProducto"
            @vaciar-carrito="vaciarCarrito"
            @pagar-compra="pagarCompra"
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