<template>
    <div id="app">
        <CuentaRegresiva></CuentaRegresiva>
    </div>
</template>

<script>
import CuentaRegresiva from './components/CuentaRegresiva.vue'

export default {
    name: 'App',
    components: {
        CuentaRegresiva
    }
}
</script>

<style>
#app {
    text-align: center;
    margin-top: 100px;
}
</style>