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
          [ ] Make a good looking display 

        [ ] Implement Loading animation on validate

        [ ] Populate Country list
    
    -->

  <div class="container">

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

    <!-- Show this only when data exists -->
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
  </div>

</template>

<script>


  export default {

    data() {
      return {
        form: {
          VATNumber: '100247019',
          country: 'EE'
        },

        items: null
      }
    },
  
    methods: {
        onSubmit(evt) {

          evt.preventDefault()

          // Using Axios to handle requests
          this.$axios
            .get(`https://vat.erply.com/numbers?vatNumber=${this.form.country}${this.form.VATNumber}`) // sends request
            .then((response) => {
              // put Response.DATA into Returned Data Object
              this.items = [response.data]
              console.log(response.status)

            }) // Handles returned data

          
        
        },
    }
  }


</script>

<style>

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

.vat-id-container > legend, .vat-returned-container > legend {
  width: auto; 
  padding: 0 20px; 
  border-bottom: none;
}

.vat-id-container > label {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}

</style>
