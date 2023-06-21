<template>
    <div id="ComponentePagos">
        <h3>Componente Pagos</h3>
        <div v-for="(info, index) in facturacionBebida" v-bind:key="index" class="contenedorPagos">
            <div>
                <p>{{  info.nombreBebidaEnviar }}</p> 
            </div>
            <div>
                <p><strong>{{  info.costoBebidaEnviar }}</strong></p>
            </div>

        </div>

        <button v-on:click.prevent="calcularCosto"> Calcular total a Pagar</button>
        <div v-if="mostrar==true">
            <p>El subtotal es: {{  acumulado }}</p>
            <p>El iva es: {{  iva }}</p>
            <p id="valorFinal">El valor final a pagar es: {{  valorFinalAPagar }}</p>
        </div>
    </div>
</template>

<script>
export default{
    name:'ComponentePagos',
    props:{
        facturacionBebida:{
            type: Array,
            required:true,
        }
    },
    data:function(){
        return{
            acumulado:0,
            iva: 0,
            valorFinalAPagar:0,
            mostrar: false,
        }
    },
    methods:{
        calcularCosto: function(){
            for(let datos of this.facturacionBebida) {
                // console.log(datos);
                this.acumulado = this.acumulado + datos.costoBebidaEnviar;
            }
            this.calcularIva();
            this.mostrar = true;
        },
        calcularIva:function(){
            this.iva = this.acumulado*19/100;
            this.valorFinalAPagar = this.acumulado + this.iva;
        }
    }
}
</script>

<style scoped>
#ComponentePagos{
    background-color: darkolivegreen;
    color:blanchedalmond;
}

.contenedorPagos{
    display: flex;
    justify-content: space-between;
}

#valorFinal{
    font-size: 25px;
    color:goldenrod;
}
</style>