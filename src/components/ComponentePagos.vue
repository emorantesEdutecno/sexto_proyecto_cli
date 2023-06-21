<template>
    <div id="ComponentePagos">
        <h3>Componente Pagos</h3>
        <p>Acumulado: {{ acumulado }}</p>
        <div v-for="(info, index) in facturacionBebida" v-bind:key="index" class="contenedorPagos">
            <div>
                <p>{{  info.nombreBebidaEnviar }}</p> 
            </div>
            <div>
                <button v-on:click.prevent="eliminarProducto(index)">Eliminar</button>
            </div>
            <div>
                <p><strong>{{  info.costoBebidaEnviar }}</strong></p>
            </div>

        </div>

        <button v-on:click.prevent="calcularCosto" id="btnPagar"> Calcular total a Pagar</button>
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
            let elBotonPagar = document.getElementById('btnPagar');
            elBotonPagar.disabled = true;

        },
        calcularIva:function(){
            this.iva = this.acumulado*19/100;
            this.valorFinalAPagar = this.acumulado + this.iva;
        },
        eliminarProducto: function(indice){
            this.mostrar=false;
            let elBotonPagar = document.getElementById('btnPagar');
            elBotonPagar.disabled = false;
            // reiniciamos a cero el acumulado porque en esta logica se recorre de nuevo el arreglo cuando se pulse el boton
            this.acumulado = 0;
            this.$emit('elementoAEliminar', indice);

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