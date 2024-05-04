<script setup>

   const props = defineProps({
      carrito:{
         type:Array,
         required:true
      }
   });

   defineEmits(['incrementar-cantidad','decrementar-cantidad','eliminar-producto','variar-carrito'])

</script>

<template>
   <nav>
      <a href="https://github.com/danielnr25" target="_blank" class="logo"><span>Carrito</span></a>
      <div class="navbar">
         <a href="#" class="btn-carrito">🛒
         </a>
         <span id="cantidad-carrito">0</span>

         <div id="carrito">

            <p class="text-center message" v-if="carrito.length === 0">El carrito esta vacio</p>

            <div v-else>
               <table class="mostrar" id="lista-carrito">
                  <thead>
                     <tr>
                        <th>Producto</th>
                        <th>Nombre</th>
                        <th>Precio</th>
                        <th>Cantidad</th>
                        <th>Oper</th>
                     </tr>
                  </thead>
                  <tbody>
                     <tr
                        v-for="(producto) in carrito"
                     >
                        <td>
                           <img 
                              :src="'/public/img/'+producto.imagen+'.jpg'" 
                              :alt="producto.nombre"
                           />
                        </td>
                        <td>{{ producto.nombre }}</td>
                        <td>{{ producto.precio}}</td>
                        <td>
                           <button
                              type="button"
                              class="restar btn"
                              @click="$emit('decrementar-cantidad',producto.id)"
                           >
                           -
                           </button>
                           {{ producto.cantidad }}
                           <button
                           class="sumar btn"
                           type="button"
                           @click="$emit('incrementar-cantidad',producto.id)"
                           >
                           +
                           </button>
                        </td>
                        <td>
                           <button 
                              @click="$emit('eliminar-producto',producto.id)"
                              class="borrar-producto"
                              type="button">
                              X
                           </button>
                        </td>
                     </tr> 
                     
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
                  <button 
                     @click="$emit('vaciar-carrito')"
                     id="vaciar-carrito"
                     type="button"
                  >
                     Vaciar
                  </button>
               </div>
            </div>

         </div>
      </div>
   </nav>
</template>

