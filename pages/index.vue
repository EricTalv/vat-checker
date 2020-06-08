<template>
    <!--
      
      TO DO 

        [*] Input for VAT- ID 
        [*] Input for Country
        [*] Country Code 

        [*] Front-end initial styles V1

        [ ] Send VAT-ID request to endpoint
        [ ] Retrieve Data 
        [ ] Display retrieved data
        [ ] Populate Country list
    
    -->

  <div class="container">

    <div class="row align-middle h-100">

      <b-form @submit="onSubmit" @reset="onReset" >

        <b-form-group
          label="VAT Identifier"
          class="border p-4 vat-id-container"
        >

          <!-- VAT ID -->
          <b-form-group label="VAT code">
            <b-form-input
              id="vat-code-input"
              type="text"         
              v-model="form.vatCode"
            ></b-form-input>
          </b-form-group>

          <!-- VAT Country -->
          <b-form-group label="VAT Country">
            <b-form-select
              id="vat-country-input"
              v-model="form.country"
              :options="[{ text: 'Choose...', value: null }, 'One', 'Two', 'Three']"
            ></b-form-select>
          </b-form-group>

          <!-- Submit -->
          <b-button block squared variant="primary" type="submit">Validate</b-button>


        </b-form-group>


      </b-form>


    </div>

  </div>

</template>

<script>

  export default {
    data() {
      return {
        form: {
          vatCode: '',
          country: ''
        }
      }
    },

    methods: {
        onSubmit(evt) {
          evt.preventDefault()
          alert(JSON.stringify(this.form))
        },


        onReset(evt) {
          evt.preventDefault()
          this.form.vatCode = ''
          this.form.country = ''
        }
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
  font-family: Consolas, sans-serif;
}

.row {
  display: flex;
  align-items: center;
  justify-content: center;

}

.vat-id-container > legend {
  width: auto; 
  padding: 0 20px; 
  border-bottom: none;
}

.vat-id-container > label {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}

</style>
