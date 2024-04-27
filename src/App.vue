<script setup>
  import {reactive,ref,onMounted} from 'vue';
  import {db} from './data/productos'
  import Producto from './components/ProductoV.vue';

  // const state = reactive({
  //   productos : db, 
  // });

  const productos = ref(db);
  //console.log(productos.value);
  
  onMounted(() =>{
    productos.value = db; // Esto nos sirve para actualizar la vista con los productos
  });

</script>


<template>
  <div>
    <div class="container">
      <!-- Navbar -->
      <nav>
         <a href="https://github.com/danielnr25" target="_blank" class="logo"><span>Carrito</span></a>
         <div class="navbar">
            <a href="#" class="btn-carrito">🛒
            </a>
            <span id="cantidad-carrito">0</span>
            <div id="carrito">
               <table class="mostrar" id="lista-carrito">
                  <thead>
                     <tr>
                        <th>Producto</th>
                        <th>Nombre</th>
                        <th>Precio</th>
                        <th>Cantidad</th>
                        <th></th>
                     </tr>
                  </thead>
                  <tbody>
                  </tbody>
                  <tfoot>
                     <tr>
                        <td colspan="2">Total</td>
                        <td id="total-pagar">0</td>
                     </tr>
                  </tfoot>
               </table>
               <div class="btns-carrito">
                  <a href="#" id="pagar-compra" onclick="pagarCompra()">Pagar</a>
                  <a href="#" id="vaciar-carrito">Vaciar</a>
               </div>
            </div>
         </div>
      </nav>

      <div id="lista-productos" class="container">
        <h1 class="titulo">Tienda de productos</h1>
        <div class="row">
          <Producto 
            v-for="producto in productos"
            :producto="producto"
          />

        </div>
      </div>
      
    </div>
  </div>
</template>