<template>
    <header>
        <div class="header-app">
            <h1><i class="fa-solid fa-clock"></i></h1>
            <h3>Tracker</h3>
        </div>
    </header>
</template>

<script lang="ts">
    import {defineComponent} from 'vue'
    export default defineComponent({
        name: 'BarraLateral'
    })
</script>

<style scoped>
header{
    padding: 1rem;
    background: #0d3b66;
    width: 100%;
    height: 100vh;
}

.header-app {
    background: #FFF;
    border-radius: 5px;
    margin: 0 5px;
    text-align: center;
}

.header-app h1 i {
    font-size: 50px;

}

@media only screen and (max-width: 768px) {
    header{
        padding: 2.5rem;
        height: auto;
    }
}
</style>
