<template>
    <section class="container pt-5">
        <div class="row">
            <div class="col">
                <SearchBar @search="searchAlbum" @reset="resetAlbum"/>
            </div>
        </div>
        <div v-if="albums != null" class="row">
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
            searchValue: "",
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
            this.searchValue = payload;
        },
        resetAlbum() {
            this.searchValue = "";
        }
    },
    computed: {
        albumsFiltered() {
            return this.albums.filter((elm) => {
                if
                (elm.title.toLowerCase().includes(this.searchValue.toLowerCase()) 
                || 
                (elm.genre == this.searchValue)) {
                    return elm;
                } 
            });
        }
    }
}
</script>

<style lang="scss" scoped>

.row {
    > *{
        width: 100%;
    }
}




@media screen and (min-width: 576px) {
    .row {
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