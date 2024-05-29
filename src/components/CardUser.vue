<template>
    <div id="carduser" class="container">
        <div class="card" style="width: ">
            <img :src="usuario.picture.large" class="card-img-top" alt="" />
            <div class="card-body">
                <h5 class="card-title"> {{ nombreCompleto }}</h5>
                <form>
                    <input class="form-control my-2" type="color" name="color"
                        id="color" v-model="mensaje.color">
                    <textarea class="form-control my-2" name="chat" id="chat"
                        v-model="mensaje.texto"
                        @keyup.enter="enviarMensaje"></textarea>
                    <br>
                    <button @click.prevent="enviarMensaje"
                        class="btn btn-info mx-5 col-7">Enviar</button>
                </form>
            </div>
        </div>
    </div>
</template>
<script>

export default {
    name: 'CardUser',
    // Props 
    props: {
        usuario: Object,
    },
    // 
    data() {
        return {
            mensaje: {
                texto: "",
                color: "",
                id: "",
            },
            }
    },
    computed: {
        nombreCompleto() {
            return `${this.usuario.name.first} ${this.usuario.name.last}`
        },

    },
    methods: {
        enviarMensaje() {
            this.mensaje.id = this.usuario.id.value
            this.mensaje.nombreCompleto = this.nombreCompleto
            this.$emit("enviarMensaje", this.mensaje)
            this.mensaje.texto = "";
        },
       
    },
  
    

}
</script>
<style scoped>
 
</style>