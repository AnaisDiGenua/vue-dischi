<template>
    <section class="container pt-5">
        <div class="row">
            <div class="col">
                <SearchBar @search="searchAlbum" @reset="resetAlbum"/>
            </div>
        </div>
        <div v-if="albums != null" class="row d-flex">
            <div v-for="album in albumsFiltered" :key="album.id">
                <AlbumCard :info="album" />
            </div>
        </div>
        <div v-else class="loader">
            Loading...
        </div>
    </section>
</template>

<script>
import axios from 'axios';
import AlbumCard from '../commons/AlbumCard.vue';
import SearchBar from '../commons/SearchBar.vue';


export default {
    name: 'AlbumsList',
    components: {
        AlbumCard,
        SearchBar
    },
    data() {
        return {
            albums: null,
            filterValue: "",
        }
    },
    created() {
        axios.get('https://flynn.boolean.careers/exercises/api/array/music ')
        .then((response) => {
            // handle success
            this.albums = response.data.response;
        })
        .catch(function (error) {
            // handle error
            console.log(error);
        });
    },
    methods: {
        searchAlbum(payload) {
            this.filterValue = payload;
        },
        resetAlbum() {
            this.filterValue = "";
        }
    },
    computed: {
        albumsFiltered() {
            return this.albums.filter((elm) => {
                if(elm.title.toLowerCase().includes(this.filterValue.toLowerCase())) {
                    return elm;
                } 
                else if(elm.genre == this.filterValue) {
                    return elm;
                }
                else if(elm.author == this.filterValue) {
                    return elm;
                }
            });
        }
    }
}
</script>

<style lang="scss" scoped>

.row {
    justify-content: center;
    > *{
        width: 70%;
    }
}




@media screen and (min-width: 576px) {
    .row {
        justify-content: flex-start;
        > *{
            width: calc(100% / 2);
        }
    }
}

@media screen and (min-width: 768px) {
    .row {
        > *{
            width: calc(100% / 4);
        }
    }
}

@media screen and (min-width: 992px) {
    .row {
        > *{
            width: calc(100% / 5);
        }
    }
}

</style>