<template>
    <div class="search">
        <form class="d-flex mb-2" action=""> 
            <input v-model="searchText" class="form-control" type="text" placeholder="Search album">
            <button class="btn lime ms-3" @click.prevent= "$emit('search', searchText)" >Search</button>
            <button class="btn btn-warning ms-2" @click.prevent= "$emit('reset', searchText) , authorValue = '', genreValue = '' " >Reset</button>
        </form>

        <select v-model= "genreValue" class="mb-4 me-2" @change= "$emit ('search', genreValue)">
            <option value="">Select genre</option>
            <option value="Rock">Rock</option>
            <option value="Pop">Pop</option>
            <option value="Jazz">Jazz</option>
            <option value="Metal">Metal</option>
        </select>
        <select v-model= "authorValue" class="mb-4" @change= "$emit ('search', authorValue)">
            <option value="">Select artist</option>
            <option value="Bon Jovi">Bon Jovi</option>
            <option value="Sting">Sting</option>
            <option value="Queen">Queen</option>
            <option value="Steve Gadd Band">Steve Gadd Band</option>
            <option value="Metal">Iron Maiden</option>
            <option value="Eric Clapton">Eric Clapton</option>
            <option value="Deep Purple">Deep Purple</option>
            <option value="Metallica">Metallica</option>
            <option value="Dave Weckl">Dave Weckl</option>
            <option value="Michael Jacjson">Michael Jackson</option>
        </select>
    </div>
    
    
</template>

<script>
export default {
    name: 'SearchBar',
    data() {
        return {
            searchText: "",
            genreValue: "",
            authorValue: ""
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