<template>
    <div class="search">
        <form class="d-flex mb-2" action=""> 
            <input v-model="searchText" class="form-control" type="text" placeholder="Search album">
            <button class="btn lime ms-3" @click.prevent= "$emit('search', searchText)" >Search</button>
            <button class="btn btn-warning ms-2" @click.prevent= "$emit('reset', searchText)" >Reset</button>
        </form>

        <select v-model= "selectVal" class="mb-4" @change= "$emit ('search', selectVal)">
            <option value="">Select genre</option>
            <option value="Rock">Rock</option>
            <option value="Pop">Pop</option>
            <option value="Jazz">Jazz</option>
            <option value="Metal">Metal</option>
        </select>
    </div>
    
    
</template>

<script>
export default {
    name: 'SearchBar',
    data() {
        return {
            searchText: "",
            selectVal: ""
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