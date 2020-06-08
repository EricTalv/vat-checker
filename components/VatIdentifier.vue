<template>
  <div class="vat-id-container">

    <div class="row align-middle h-50">

      <b-form @submit="onSubmit" class="w-50">

        <b-form-group
          label="VAT Identifier"
          class="border p-4 vat-id-container"
        >

          <!-- VAT ID -->
          <b-form-group label="VAT Number">
            <b-form-input
              id="vat-number-input"
              type="text"         
              v-model="form.VATNumber"
              size="lg"
            ></b-form-input>
          </b-form-group>

          <!-- VAT Country -->
          <b-form-group label="VAT Country">
            <b-form-select
              id="vat-country-input"
              v-model="form.country"
              :options="['EE', 'BG', 'RU']"
              size="lg"

            ></b-form-select>
          </b-form-group>

          <!-- Submit -->
          <b-button block squared size="lg" variant="primary" type="submit">Validate</b-button>

        </b-form-group>

      </b-form>

    </div>

    <!-- Show loading when retrieving data -->
      <div class="row text-center">
        <b-spinner v-if="isRetrieving" style="width: 3.5rem; height: 3.5rem;" variant="primary" type="grow" label="Spinning"></b-spinner>
      </div>
    
    <!-- Show this only when data exists -->
    <transition name="fade">
      <div class="row" v-if="items">
        <b-col>
          <b-form-group
            label="Result"
            class="border p-4 vat-returned-container"
          >

            <b-table stacked :items="items"></b-table>

          </b-form-group>  
        </b-col>
      </div> 
    </transition>
  </div>
</template>

<script scoped>
export default {
    name: "VatIdentifier",
    data() {
      return {
        form: {
          VATNumber: '100247019',
          country: 'EE'
        },

        items: null,
        isRetrieving: false,
      }
    },
  
    methods: {
        onSubmit(evt) {

          evt.preventDefault()

          // Set loading animation
          this.isRetrieving = true

          // Using Axios to handle requests
          this.$axios
            // Send request to url
            .get(`https://vat.erply.com/numbers?vatNumber=${this.form.country}${this.form.VATNumber}`) // sends request
            // How we handle the response
            .then((response) => {
              // put Response.DATA into Returned Data Object
              this.items = [response.data]
              // set loading to false
              this.isRetrieving = false
            }) 
         
        
        },
    }
}
</script>

<style>

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}

html, body {
  margin: 0;
  padding: 0;
}

.container { 
  height: 90vh;
  font-family:'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  font-size: 20px;
}

.row {
  display: flex;
  align-items: center;
  justify-content: center;

}

.vat-id-container, .vat-returned-container {
  border-radius: 10px;
  box-shadow: 0px 18px 42px -24px rgba(0,0,0,0.42);
}

.vat-id-container > legend, .vat-returned-container > legend {
  width: auto; 
  padding: 0 20px; 
  border-bottom: none;
}

.vat-id-container > label {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}
</style>