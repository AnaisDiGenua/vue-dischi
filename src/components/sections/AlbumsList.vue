<template>
    <section class="container pt-5">
        <div v-if="albums != null" class="row">
            <div v-for="album in albums" :key="album.id">
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

export default {
    name: 'AlbumsList',
    components: {
        AlbumCard
    },
    data() {
        return {
            albums: null
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