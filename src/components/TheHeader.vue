<script>
import axios from "axios";


export default {
    components : {
    
    },

    data() {
        return {
            mostri: [],
            paggInfo: {},
            pagecurrent: 1,

        };
    },
    methods: {
        fetchMostri(nexturl) {
            const url = nexturl ?? `https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0`;   
            // const url = nexturl ? nexturl : `https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0`;       secondo metodo
            axios.get(url).then((response) => {
                this.mostri = response.data.data;
                this.paggInfo = response.data.meta;
            });
        },
        fetchbextpage() {
            this.fetchMostri(this.paggInfo.next_page)

        }
    },
    mounted() {
        this.fetchMostri();
    }
};
</script>



<template>
    <div class="sfondo p-3">
        <div class="p-3">
            <input type="text" class="p-1 g-4">
        <button type="button" class="btn btn-light">Cerca</button>
        </div>

        <div class="container bg p-4">
            
            <div class=" p-3 bg-dark text-white">Found {{  }}card</div>
            <div class="row row-col-2 g-4">
                <div class="col" v-for="mostro in mostri" :key="mostro.id">
                    <div class="card sfondo h-100 ">
                        <img  :src="mostro.card_images[0].image_url" alt="" class="card-img-top carte p-2">
                        <div class="card-body type">
                            <h5 class="card-title text-white">{{ mostro.name }}</h5>
                            <p class="card-text">{{ mostro.archetype }}</p>
                        </div>
                    </div>
                </div>
            </div>
            
        </div> 
        <div class="text-center p-2">
            <button @click="fetchbextpage" type="button" class="btn btn-centrato btn-light">Di piu</button>
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

.type {
    text-align: center;
}


</style>
<!--    -->