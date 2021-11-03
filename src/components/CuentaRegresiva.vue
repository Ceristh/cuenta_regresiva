<template>
    <div id="app">
        <h1>Cuenta Regresiva</h1>
        <h2 class="mb-5">{{regresion(tictac)}}</h2>
        <button type="button" class="caja btn btn-info" v-for="descuento in caja" :key="descuento" @click="cuentaRegresiva(descuento.tiempo)">{{descuento.name}}</button>
    </div>
</template>
<script>
export default {
    name: 'CuentaRegresiva',
    data() {
        return {
            tictac: 0,
            caja: [
                {name: '3 segundos', tiempo: 3},
                {name: '5 segundos', tiempo: 5},
                {name: '10 segundos', tiempo: 10},
                {name: '30 segundos', tiempo: 30},
                {name: '1 minuto', tiempo: 60},
                {name: '10 minutos', tiempo: 600},
            ],
            intervalo: '',
            estado: {activo: false},
        }
    },
    methods: {
        regresion: function(tictac) {
            let segundos = ('0' + Math.floor(tictac % 60)).slice(-2);
            let minutos = ('0' + Math.floor(tictac / 60 % 60)).slice(-2);
            return `${minutos}:${segundos} min|seg`
        },
        cuentaRegresiva: function(cuenta) {
            this.tictac = cuenta;
            this.estado.activo = true;
            this.intervalo = setInterval(() => {
                if (this.tictac > 0) {
                    this.tictac --;
                } else {
                    clearInterval(this.intervalo)
                }
            },1500)
        }
    },
}
</script>
<style>
.caja {
    margin: 5px;
}
#app h1 {
    font-size: 5rem;
    color: #1ca099;
}
#app h2 {
    font-size: 6rem;
    color: #2d219c;
}
</style>