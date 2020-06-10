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

            <div class="row" v-if="successStatus">
              <b-alert 
                v-model="alertShow"
                @dismissed="dismissCountDown=0" 
                :variant="successStatus" 
                dismissible
              >
                {{ requestMessage }}
              </b-alert> 
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
          VATNumber: '',
          country: ''
        },

        alertShow: false,
        successStatus: null,
        requestMessage: '',

        VatData: null,
        isRetrieving: false,
      }
    },

    methods: {


        // This gets the country from my CountryDropdown component
        // and passes it here (parent) into the form
        getCountry(country) {
            this.form.country = country
        },
        onSubmit(evt) {

          evt.preventDefault()

          // Set loading animation
          this.isRetrieving = true

          // Empty Alert
          this.alertShow = false
          this.successStatus = null
          this.requestMessage = ''

          // Using Axios to handle requests
          this.$axios
            // Send request to url
            .get(`https://vat.erply.com/numbers?vatNumber=${this.form.country}${this.form.VATNumber}`) // sends request
            // How we handle the response
            .then((response) => {
            
              // Request Alert Parameters if SUCCESS
              this.successStatus = 'success' 
              this.requestMessage = 'Request was Successful!'
              this.alertShow = true;

              console.log(response)

              // Send data to parent
              this.$emit('setVatData', response.data)

              // set loading to false
              this.isRetrieving = false
            }) 
            .catch(error => {
              
              // Request Alert Parameters if ERROR
              this.successStatus = 'danger' 
              this.requestMessage = `Request was Unsuccessful -> (${error.response.status}) ${error.response.data.error}`
              this.alertShow = true;

              // Resets data, delete this if you want to keep previous data
              this.$emit('setVatData', error.data)

              // set loading to false
              this.isRetrieving = false
            })
        },
    }
}

</script>