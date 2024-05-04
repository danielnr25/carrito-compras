<script setup>
   import { computed } from 'vue';


   const props = defineProps({
      carrito:{
         type:Array,
         required:true
      },
      cantidadCarrito:{
         type:Number,
         required:true
      }
    
   });
 

   defineEmits(['incrementar-cantidad','decrementar-cantidad','eliminar-producto','variar-carrito','pagar-compra']);

   const totalPagar = computed( () =>{
      return props.carrito.reduce((total,producto) =>
         total + (producto.precio * producto.cantidad),0);
   })


</script>

<template>
   <nav>
      <a href="https://github.com/danielnr25" target="_blank" class="logo"><span>Carrito</span></a>
      <div class="navbar">
         <a href="#" class="btn-carrito">🛒
         </a>
         <span id="cantidad-carrito">{{cantidadCarrito}}</span>
      
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
                        <th>Subtotal</th>
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
                        <td>$ {{ producto.precio}}</td>
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
                           $ {{ producto.precio * producto.cantidad }}
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
                        <td colspan="4">Total a pagar</td>
                        <td id="total-pagar">$ {{ totalPagar }}</td>
                     </tr>
                  </tfoot>
               </table>
               <div class="btns-carrito">
                  <button 
                     @click="$emit('pagar-compra')"
                     id="pagar-compra"
                     type="button"
                  >
                     Pagar Compra
                  </button>

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

