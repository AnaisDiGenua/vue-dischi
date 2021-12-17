<template>
    <header>
        <img src="../../assets/img/logo-small.svg" alt="logo spotify">
    </header>
</template>

<script>
export default {
    name: 'Header'
}
</script>

<style lang="scss" scoped>
@import '../../assets/style/partials/variables.scss';

header {
    height: 70px;
    line-height: 70px;
    background-color: $primaryColor;

    img {
        width: 50px;
        margin-left: 20px;
        vertical-align: middle;
    }
}
</style>