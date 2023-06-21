<template>
    <div id="ComponentePadre">
        <h2>Componente Padre</h2>
        <div class="container">
            <div class="row">
                <div class="col-md-9">
                    <ComponenteProductos
                        v-bind:informacionBebidas =datosCards
                        v-on:bebidaSeleccionada="procesarBebidaSeleccionada"
                    />
                </div>
                <div class="col-md-3">
                    <ComponentePagos 
                        v-bind:facturacionBebida="arregloProductosSeleccionados"
                        v-on:elementoAEliminar = "procesarElementoAEliminar"
                    />
                </div>
            </div>
        </div>
    </div>
</template>


<script>
import ComponenteProductos from '@/components/ComponenteProductos.vue';
import ComponentePagos from '@/components/ComponentePagos.vue';
export default{
    name: 'ComponentePadre',
    components:{
        ComponenteProductos,
        ComponentePagos
    },
    data: function(){
        return{
            // datosCards es un arreglo de objetos
            datosCards:[
            {
                imagenBebida:'https://cdn0.recetasgratis.net/es/posts/5/9/6/cola_de_mono_chileno_19695_600.webp',
                tituloBebida:'Cola de Mono',
                descripcionBebida:'El cola de mono o colemono es una bebida tradicional de épocas decembrinas en Chile y algunas partes de Perú, se prepara a base de un aguardiente de uvas llamado pisco, pero se puede sustituir con otro tipo de aguardiente o vodka. Además, también lleva leche, azúcar, café y algunas especias para dar sabor, tales como la cáscara de naranja, la canela, los clavos de olor, la vainilla o la nuez moscada',
                costo: 12000
            },
            {
                imagenBebida:'https://cdn0.recetasgratis.net/es/posts/4/3/6/terremoto_chileno_74634_600.webp',
                tituloBebida:'Terremoto',
                descripcionBebida:'El trago terremoto se hizo popular en Chile a finales del siglo XX y ahora forma parte de las fiestas patrias celebradas el 18 y 19 de Septiembre. Se prepara con vino pipeño, granadina y helado de piña y es común encontrarlo en bares, restaurantes y puestos de comida. La historia más popular sobre el nombre de este trago habla sobre un terremoto que hubo en 1985. Los terremotos forman parte de la idiosincrasia chilena, por ello son aceptados y parte se su historia.',
                costo: 22000
            },
            {
                imagenBebida:'https://www.cocina-chilena.com/base/stock/Recipe/365-image/365-image_web.jpg',
                tituloBebida:'Malta con Huevo',
                descripcionBebida:'Es una bebida típica muy nutritiva que se ingiere en el invierno en Chile.',
                costo: 13000
            },
            {
                imagenBebida:'https://www.tragosdelmundo.cl/wp-content/uploads/2019/10/jote-calimocho.png',
                tituloBebida:'Jote',
                descripcionBebida:'Este combinado no es nada más que una mezcla de vino tinto con coca cola. El Jote es un típico trago chileno, aunque también existe en otros países con distintos nombres: (Calimocho, Rioja, Tincola, Mocho)',
                costo: 17000
            },
            {
                imagenBebida:'https://www.recetasnestlecam.com/sites/default/files/styles/recipe_detail_desktop/public/srh_recipes/5338c89f4cf8fbd2a8211fb423c88751.webp?itok=ty-AWxmH',
                tituloBebida:'Chocoron',
                descripcionBebida:'Bebida que no le gusta a Maria Fernanda Avello',
                costo: 25000
            },
            {
                imagenBebida:'https://elsoldeiquique.cl/wp-content/uploads/2018/11/pichi-canguro.png',
                tituloBebida:'Pichi de Canguro',
                descripcionBebida:'La mezcla es fácil, vierte en un vaso de vidrio, ya que de plástico le da un sabor medio amargoso, el vino en caja (cartoné para los pitucos) y luego, poco a poco la bebida. Deja reposar unos segundos y salú.',
                costo: 16000
            }

            ],
            arregloProductosSeleccionados:[],
        }
    },
    methods:{
        procesarBebidaSeleccionada: function(indiceBebida){
            // console.log('indice de bebida recibida por el padre: ', indiceBebida);
            let objetoIdentificadoBebida = this.datosCards[indiceBebida];
            let objetoAEnviar = {
                nombreBebidaEnviar: objetoIdentificadoBebida.tituloBebida,
                costoBebidaEnviar: objetoIdentificadoBebida.costo,
            };
            this.arregloProductosSeleccionados.push(objetoAEnviar);
            
        },
        procesarElementoAEliminar: function(indiceAEliminar){
            this.arregloProductosSeleccionados.splice(indiceAEliminar,1);
        }
    }
}
</script>

<style scoped>
#ComponentePadre{
    background-color: greenyellow;
}
</style>