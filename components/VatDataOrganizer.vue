<template>
     <transition name="fade">
         <div class="vat-returned-wrapper w-100">
            <div class="row ">
                <b-col>
                <b-form-group
                    label="Result"
                    class="border p-4 vat-returned-container"
                >

                    <b-table stacked :items="parentItems"></b-table>
                </b-form-group>  
                </b-col>
            </div>              
        </div>    
    </transition>
</template>

<script>

export default {
    props: { 
        parentItems: Array,

    }
}

</script>