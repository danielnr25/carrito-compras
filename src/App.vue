<script setup>
  
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

      <!-- Tienda -->
      <div id="lista-productos" class="container">
         <h1 class="titulo">Tienda de productos</h1>
         <div class="row">
            <div class="card">
               <img src="/public/img/product1.jpg" alt="">
               <div class="card-header">
                  <h3>Polo adidas small</h3>
                  $<span>75</span>
                  <a href="#" class="agregar-carrito" data-id="1">Agregar carrito</a>
               </div>
            </div>
            <div class="card">
               <img src="/public/img/product2.jpg" alt="">
               <div class="card-header">
                  <h3>Audifonos Bluetooth</h3>
                  $<span>79</span>
                  <a href="#" class="agregar-carrito" data-id="2">Agregar carrito</a>
               </div>
            </div>
            <div class="card">
               <img src="/public/img/product3.jpg" alt="">
               <div class="card-header">
                  <h3>Casaca con capucha </h3>
                  $<span>120</span>
                  <a href="#" class="agregar-carrito" data-id="3">Agregar carrito</a>
               </div>
            </div>
            <div class="card">
               <img src="/public/img/product4.jpg" alt="">
               <div class="card-header">
                  <h3>Tomado unisex </h3>
                  $<span>17</span>
                  <a href="#" class="agregar-carrito" data-id="4">Agregar carrito</a>
               </div>
            </div>
            <div class="card">
               <img src="/public/img/product5.jpg" alt="">
               <div class="card-header">
                  <h3>Lentes primaverales </h3>
                  $<span>90</span>
                  <a href="#" class="agregar-carrito" data-id="5">Agregar carrito</a>
               </div>
            </div>
            <div class="card">
               <img src="/public/img/product6.jpg" alt="">
               <div class="card-header">
                  <h3>Gorra negra adidas</h3>
                  $<span>12</span>
                  <a href="#" class="agregar-carrito" data-id="6">Agregar carrito</a>
               </div>
            </div>
            <div class="card">
               <img src="/public/img/product7.jpg" alt="">
               <div class="card-header">
                  <h3>Mochila viajera</h3>
                  $<span>59</span>
                  <a href="#" class="agregar-carrito" data-id="7">Agregar carrito</a>
               </div>
            </div>
            <div class="card">
               <img src="/public/img/product8.jpg" alt="">
               <div class="card-header">
                  <h3>Zapatillas running</h3>
                  $<span>125</span>
                  <a href="#" class="agregar-carrito" data-id="8">Agregar carrito</a>
               </div>
            </div>
            <div class="card">
               <img src="/public/img/product9.jpg" alt="">
               <div class="card-header">
                  <h3>Polerea con capucha de básquet</h3>
                  $<span>125</span>
                  <a href="#" class="agregar-carrito" data-id="9">Agregar carrito</a>
               </div>
            </div>
            <div class="card">
               <img src="/public/img/product10.jpg" alt="">
               <div class="card-header">
                  <h3>Gorro beanie adventure</h3>
                  $<span>45</span>
                  <a href="#" class="agregar-carrito" data-id="10">Agregar carrito</a>
               </div>
            </div>
            <div class="card">
               <img src="/public/img/product11.jpg" alt="">
               <div class="card-header">
                  <h3>Zapatillas Samba OG</h3>
                  $<span>235</span>
                  <a href="#" class="agregar-carrito" data-id="11">Agregar carrito</a>
               </div>
            </div>
            <div class="card">
               <img src="/public/img/product12.jpg" alt="">
               <div class="card-header">
                  <h3>Short de básquet legends</h3>
                  $<span>125</span>
                  <a href="#" class="agregar-carrito" data-id="12">Agregar carrito</a>
               </div>
            </div>
         </div>
      </div>
    </div>
  </div>
</template>