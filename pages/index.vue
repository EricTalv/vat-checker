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

        [ ] Turn everything into a component
         [ ] Vat identifier Component
         [ ] City Population component

        [ ] Populate Country list
    
    -->

  <div class="container">

    <vat-identifier />

  </div>

</template>

<script>
import VatIdentifier from "~/components/VatIdentifier.vue"

  export default {
    components: {
      VatIdentifier
    }
  }

</script>

<style>


</style>
