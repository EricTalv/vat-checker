<template>
    <v-select 
        @input="setSelected" 
        label="countryName" 
        :options="countries"
    >
        <template
            #search="{attributes, events}"
        >
            <input
                class="vs__search"            
                :required="!selected"
                v-bind="attributes"
                v-on="events"
            />
        </template>
    </v-select>
</template>

<script>
import countryData from '~/json/countries.json'

export default {
    data() {
        return {
            selected: '',



            countries: countryData,
        }
    },

    methods: {
        setSelected(value){
           this.selected = value.countryCode
           this.$emit("selected", value.countryCode)
        }
    }
}

</script>