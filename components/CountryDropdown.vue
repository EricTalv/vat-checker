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

export default {
    data() {
        return {
            selected: '',

            countries: [
                { countryCode: 'EE', countryName: 'Estonia' },
                { countryCode: 'RU', countryName: 'Russia' },
                { countryCode: 'BG', countryName: 'Bulgaria' }
            ]
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