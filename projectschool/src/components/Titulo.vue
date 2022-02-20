<template>
    <div>
        <h1>{{texto}}</h1>
    </div>
</template>

<script>
    export default {
        name: 'Titulo',
        props: {
            texto: String
        }
    }
</script>

<style lang="css" scoped>
h1{
    margin-bottom: 20px;
}
</style>