<template>
    <!--
      
      TO DO 

        [*] Input for VAT- ID 
        [*] Input for Country
        [*] Country Code 

        [*] Front-end initial styles V1

        [*] Send VAT-ID request to endpoint
          [*] send a -succesful- request to url
        [*] Retrieve Data 
        [*] Display retrieved data

        [*] Prettify JSON
        [*] Return data Form
          [*] Make a good looking display 

        [*] Implement Loading animation on validate

        [*] Turn everything into a component
         [*] Vat identifier Component
         [ ] City Population component
         [*] Data-organizer component

        [*] Populate Country list

        [ ] Error handling

        [ ] Fix-up Documentation
    
    -->

  <div class="container">

    <vat-compiler/>

  </div>

</template>

<script>
import VatCompiler from "~/components/VatCompiler.vue"

  export default {
    components: {
      VatCompiler
    }
  }

</script>

<style>


</style>
