<template>
    <div id="EventModifierCapture">
        <h2>Event Modifier Capture</h2>
            <div id="abuelo"
            v-on:click.capture="saludo('Hola soy abuelo capture')"
            v-on:click="saludo('Hola soy abuelo bubbling')">
                div abuelo
                <!-- no detenemos la propagación del evento click en los ancestros del div padre-->
                <div id="padre" 
                v-on:click.capture="saludo('Hola soy padre capture')"
                v-on:click="saludo('Hola soy padre bubbling')">
                    div padre
                    <!-- detenemos (stop) la propagación del evento click en los demás ancestros del div hijo-->
                    <div id="hijo"
                    v-on:click.capture="saludo('Hola soy hijo capture')"
                    v-on:click="saludo('Hola soy hijo bubbling')">
                        div hijo

                    </div>
                </div>
            </div>
    </div>
</template>

<script>
export default{
    name:'EventModifierCapture',
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
#EventModifierCapture{
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