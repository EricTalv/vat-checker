<template>
  <div class="vat-comp-wrapper">

    <!-- VAT IDENTIFIER -->
    <!-- API handeling is here -->
    <VatIdentifier @setVatData="setVatData($event)" />

    <!-- VAT Data organizer -->
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