<template>
    <main>

        <AlbumsList/>

    </main>
</template>

<script>
import AlbumsList from '../sections/AlbumsList.vue'

export default {
    name: 'Main',
    components: {
        AlbumsList
    }
}
</script>

<style lang="scss" scoped>
@import '../../assets/style/partials/variables.scss';

main {
    background-color: $secondaryColor;
}
</style>