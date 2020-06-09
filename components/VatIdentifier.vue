<template>
    <div class="vat-id-wrapper">

        <div class="row my-5">

            <b-form @submit="onSubmit" class="w-100">

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
                    required
                ></b-form-input>
                </b-form-group>

                <!-- VAT Country -->
                <b-form-group label="VAT Country">
                
                <!-- Country Dropdown List -->
                <CountryDropdown  v-on:selected="getCountry" />

                </b-form-group>

                <!-- Submit -->
                <b-button block squared size="lg" variant="primary" type="submit">Validate</b-button>

            </b-form-group>

            </b-form>

            <!-- Show loading when retrieving data -->
            <div class="row mx-auto" v-if="isRetrieving">
            <b-spinner style="width: 3rem; height: 3rem;" variant="primary" type="grow" label="Spinning"></b-spinner>
            </div>

        </div>
    </div>
</template>

<script>
import CountryDropdown from '~/components/CountryDropdown.vue'

export default {
     components: {
       CountryDropdown
     },
     data() {
      return {
        form: {
          VATNumber: '100247019',
          country: 'EE'
        },

        VatData: null,
        isRetrieving: false,
      }
    },

    methods: {
        getCountry(country) {
            this.form.country = country
        },
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
            
              // Send data to parent
              this.$emit('setVatData', response.data)

              // set loading to false
              this.isRetrieving = false
            }) 
         
        
        },
    }
  
}

</script>