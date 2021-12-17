<template>
    <div class="album text-center p-3 mb-4">
        <img class="mb-3" :src="info.poster" alt="">
        <h4>{{info.title}}</h4>
        <p class="mb-0">{{info.author}}</p>
        <p>{{info.year}}</p>
    </div>
</template>

<script>
export default {
    name: 'AlbumCard',
    props: {
        info: Object
    }
}
</script>

<style lang="scss" scoped>
@import '../../assets/style/partials/variables.scss';


.album{
    min-height: 430px;
    background-color: $primaryColor;

    img {
        width: 100%;
    }

    h4 {
        text-transform: uppercase;
        color: #fff;
    }

    p {
        color: lightgray;
    }
}

</style>