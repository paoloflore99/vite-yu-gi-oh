
<script>

import { store, filtromostri } from "../store";


export default {
    components: {

    },
    data () {
        return {
            searchThext: "",
            store,


        }
    }, 
    methods: {
        filtromostri ,

        watch: {
        'store.searchText': function (nuovoText) {
            this.mostri = [];
            this.fetchMostri(
                `https://db.ygoprodeck.com/api/v7/cardinfo.php?name=${store.nuovoText}`
                );
        },
    },
    }

}
</script>



<template>
    <div class="p-3">
        <input type="text" class="p-1 g-4" v-model="store.searchThext">
        <button type="button" class="btn btn-light" @click="filtromostri">Cerca</button>
    </div>
</template>


<!-- searchThext -->

<style lang="scss" scoped></style>