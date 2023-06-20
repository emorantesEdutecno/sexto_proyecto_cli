<template>
    <div id="ComponenteProductos">
            <h3>Componente Productos</h3>
            <!-- {{  informacionBebidas }} -->

            <h4>Generacion de Contenido dinamicamente con v-for</h4>
            <div class="container">
                <div class="row">
                    <div v-for="(datos,index) in informacionBebidas" :key="index" class="col">
                        <div class="card" style="width: 18rem;">
                                <img v-bind:src="datos.imagenBebida" class="card-img-top" v-bind:alt="datos.tituloBebida">
                                <div class="card-body">
                                    <h5 class="card-title">{{ datos.tituloBebida }}</h5>
                                    <p class="card-text">{{  datos.descripcionBebida }}</p>
                                    <a href="#" class="btn btn-primary" v-on:click.prevent="agregarBebida(index)">Agregar</a>
                                </div>
                            </div>
                    </div>
                </div>
            </div>




            <h4>Utilizacion de la maqueta estatica</h4>
            <div class="container">
                <div class="row">
                    <div class="col-md-4 bg-warning">
                            <div class="card" style="width: 18rem;">
                                <img v-bind:src="informacionBebidas[0].imagenBebida" class="card-img-top" v-bind:alt="informacionBebidas[0].tituloBebida">
                                <div class="card-body">
                                    <h5 class="card-title">{{ informacionBebidas[0].tituloBebida }}</h5>
                                    <p class="card-text">{{ informacionBebidas[0].descripcionBebida }}</p>
                                    <a href="#" class="btn btn-primary" v-on:click.prevent="agregarBebida(0)">Agregar</a>
                                </div>
                            </div>
                    </div>
                    <div class="col-md-4">
                            <div class="card" style="width: 18rem;">
                                <img v-bind:src="informacionBebidas[1].imagenBebida" class="card-img-top" v-bind:alt="informacionBebidas[0].tituloBebida">
                                <div class="card-body">
                                    <h5 class="card-title">{{ informacionBebidas[1].tituloBebida }}</h5>
                                    <p class="card-text">{{  informacionBebidas[1].descripcionBebida }}</p>
                                    <a href="#" class="btn btn-primary">Agregar</a>
                                </div>
                            </div>
                    </div>
                    <div class="col-md-4">
                            <div class="card" style="width: 18rem;">
                                <img src="https://lh3.googleusercontent.com/-gaBV0BnRBPU/Yz447FQ63-I/AAAAAAAAuYQ/37Bn-ZFZ-coy1VHz9XugLWHFRib-IOnUgCNcBGAsYHQ/w1200-h630-p-k-no-nu/Kimetsu-no-Yaiba.jpg" class="card-img-top" alt="...">
                                <div class="card-body">
                                    <h5 class="card-title">Card title</h5>
                                    <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
                                    <a href="#" class="btn btn-primary">Go somewhere</a>
                                </div>
                            </div>
                    </div>
                </div>
                <div class="row">
                    <div class="col-md-4">
                            <div class="card" style="width: 18rem;">
                                <img src="https://lh3.googleusercontent.com/-gaBV0BnRBPU/Yz447FQ63-I/AAAAAAAAuYQ/37Bn-ZFZ-coy1VHz9XugLWHFRib-IOnUgCNcBGAsYHQ/w1200-h630-p-k-no-nu/Kimetsu-no-Yaiba.jpg" class="card-img-top" alt="...">
                                <div class="card-body">
                                    <h5 class="card-title">Card title</h5>
                                    <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
                                    <a href="#" class="btn btn-primary">Go somewhere</a>
                                </div>
                            </div>
                    </div>
                    <div class="col-md-4 bg-danger">
                            <div class="card" style="width: 18rem;">
                                <img src="https://lh3.googleusercontent.com/-gaBV0BnRBPU/Yz447FQ63-I/AAAAAAAAuYQ/37Bn-ZFZ-coy1VHz9XugLWHFRib-IOnUgCNcBGAsYHQ/w1200-h630-p-k-no-nu/Kimetsu-no-Yaiba.jpg" class="card-img-top" alt="...">
                                <div class="card-body">
                                    <h5 class="card-title">Card title</h5>
                                    <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
                                    <a href="#" class="btn btn-primary">Go somewhere</a>
                                </div>
                            </div>
                    </div>
                    <div class="col-md-4">
                            <div class="card" style="width: 18rem;">
                                <img src="https://lh3.googleusercontent.com/-gaBV0BnRBPU/Yz447FQ63-I/AAAAAAAAuYQ/37Bn-ZFZ-coy1VHz9XugLWHFRib-IOnUgCNcBGAsYHQ/w1200-h630-p-k-no-nu/Kimetsu-no-Yaiba.jpg" class="card-img-top" alt="...">
                                <div class="card-body">
                                    <h5 class="card-title">Card title</h5>
                                    <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
                                    <a href="#" class="btn btn-primary">Go somewhere</a>
                                </div>
                            </div>
                    </div>
                </div>
            </div>
    </div>
</template>

<script>
export default{
    name:'ComponenteProductos',
    props:{
        informacionBebidas:{
            type: Array,
            required: true,
        },

    },
    data: function(){
        return{

        }
    },
    methods:{
        agregarBebida: function(indice){
            console.log('indice de la bebida seleccionada desde el hijo: ', indice);
            this.$emit('bebidaSeleccionada', indice);
        }
    }
}
</script>

<style scoped>
#ComponenteProductos{
    background-color: aquamarine;
}
</style>
