<template>
  <div class="vat-id-wrapper">

    <!-- VAT IDENTIFIER -->
    <VatIdentifier @setVatData="setVatData($event)" />

    <!-- VAT Data organizer -->
    <!-- Pass data to Data-Organizer component -->
    <!-- Show this only when data exists -->
    <VatDataOrganizer v-bind:parentItems="[VatData]" v-if="VatData"/>

  </div>
</template>

<script scoped>
import VatDataOrganizer from "~/components/VatDataOrganizer.vue";
import VatIdentifier from "~/components/VatIdentifier.vue";

export default {
    name: "VatCompiler",
    components: {
      VatDataOrganizer,
      VatIdentifier
    },

    data() {
      return {
       
        VatData: null,
      }
    },

    methods: {
      setVatData (data) {
        this.VatData = data
      }
    }
  
    
}
</script>

<style>

</style>