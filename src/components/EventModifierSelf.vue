<template>
    <div id="EventModifierSelf">
        <h2>Event Modifier Self</h2>
            <div id="abuelo" v-on:click="saludo('Hola soy abuelo')">
                div abuelo
                <!-- al colocar el modificador self en el evento click del padre, no se va a propagar el evento click en el padre -->
                <!-- el único que puede invocar saludo() desde el padre, sería hacer click unicamente en el div padre -->
                <div id="padre" v-on:click.self="saludo('Hola soy padre')">
                    div padre

                    <div id="hijo" v-on:click="saludo('Hola soy hijo')">
                        div hijo

                    </div>
                </div>
            </div>
    </div>
</template>

<script>
export default{
    name:'EventModifierSelf',
    data: function(){
        return{

        }
    },
    methods:{
        saludo: function(str){
            alert(str);
        }
    }
}
</script>

<style scoped>
#EventModifierSelf{
    background-color: floralwhite;
}

#abuelo{
    width: 300px;
    height: 300px;
    font-size: 30px;
    background-color: gray;
    margin: 0 auto;
}

#padre{
    width: 200px;
    height: 200px;
    font-size: 25px;
    background-color:bisque;
    margin: 0 auto; 
    position: relative;
    top: 10%;
}

#hijo{
    width: 100px;
    height: 100px;
    font-size: 20px;
    background-color:aquamarine;
    margin: 0 auto; 
    position: relative;
    top: 10%;
}
</style>