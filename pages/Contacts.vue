<template>
  <div class="container">
    <h1>Contacts</h1>
  </div>
</template>

<script>
  export default {
    name: 'Contact',
    head: {
      title: 'Pagina de contactos'
    },
    layout: 'contact', // Usa una plantilla personalizada llamada '/layouts/contact.vue'.
                // Sí al componente no se le establece  la propiedad 'layout' utilizará el que viene 
                // por defecto: 'default.vue'.
                // Todos las plantillas están ubicadas en la carpeta '/layouts/default.vue'
  }
</script>