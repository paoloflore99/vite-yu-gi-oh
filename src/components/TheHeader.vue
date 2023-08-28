<script>
import axios from "axios";

export default {
    data() {
        return {
            mostri: []
        };
    },
    methods: {
        fetchMostri() {
            const url = `https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0`;         
            axios.get(url).then((response) => {
                this.mostri = response.data.data;
            });
        }
    },
    mounted() {
        this.fetchMostri();
    }
};
</script>



<template>
    <div class="sfondo p-3">
        <input type="text" class="p-1 g-4">
        <div class="container bg p-4">
            
            <div class=" p-3 bg-dark text-white">Found 39card</div>
            <div class="row row-col-2 g-4">
                <div class="col" v-for="mostro in mostri" :key="mostro.id">
                    <div class="card sfondo h-100 ">
                        <img :src="mostro.card_images[0].image_url" alt="" class="card-img-top carte">
                        <div class="card-body">
                            <h5 class="card-title text-white">{{ mostro.name }}</h5>
                            <p class="card-text">{{ mostro.archetype }}</p>
                        </div>
                    </div>
                </div>
            </div>
            
        </div>
    </div>
    </template>
    

    

<style lang="scss" scoped>
.sfondo {
    background-color: rgb(226, 155, 49);
}

.bg {
    background-color: aliceblue;
}

.carte {
    width: 200px;
}
</style>
