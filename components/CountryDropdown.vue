<template>
    <v-select :value="selected.countryName" @input="setSelected" label="countryName" :options="countries" />
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