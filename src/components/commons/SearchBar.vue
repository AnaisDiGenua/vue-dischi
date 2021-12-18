<template>
    <div class="search-bar mb-4">
        <form class="d-flex" action="">
            <input v-model="searchText" class="form-control" type="text" placeholder="Search album">
            <button class="btn lime ms-3" @click.prevent= "$emit('search', searchText)" >Search</button>
            <button class="btn btn-warning ms-2" @click.prevent= "$emit('reset', searchText)" >Reset</button>
        </form>
    </div>
</template>

<script>
export default {
    name: 'SearchBar',
    data() {
        return {
            searchText: ''
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../../assets/style/partials/variables.scss';

.btn.lime {
    background-color: $brandColor;
}
</style>