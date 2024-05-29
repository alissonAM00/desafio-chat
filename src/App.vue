<template>
  <div id="app" class="container">
    <h1 class="text-center my-5">Chat Room</h1>
    <main class="my-5 container">
      <div class="row">
        <div class="col-3">
          <CardUser
            :usuario="usuarios[0]"
            @enviarMensaje="enviarMensajeHandler"
          />
        </div>
        <div class="col-5">
          <ChatUser :mensajes="mensajes" :usuarios="usuarios" />
        </div>
        <div class="col-3">
          <CardUser
            :usuario="usuarios[1]"
            @enviarMensaje="enviarMensajeHandler"
          />
        </div>
      </div>
    </main>
  </div>
</template>

<script>

import axios from "axios";
import CardUser from "./components/CardUser.vue";
import ChatUser from "./components/ChatUser.vue";


export default {
  name: "App",
  components: {
    CardUser,
    ChatUser,
  },

  //
  data() {
    return {
      usuarios: [],
      mensajes: [],
    };
  },

  // Este método es el que llama a la información de la Api, por eso usamos Axios.get
  methods: {
    async getPerson() {
      try {
        let response = await axios.get("https://randomuser.me/api/?results=2");
        this.usuarios = response.data.results;
      } catch (error) {
        console.log(error);
      }
    },
    
    enviarMensajeHandler(mensaje) {
            let nuevoMensaje = {
                id: mensaje.id,
                color: mensaje.color,
                nombreCompleto: mensaje.nombreCompleto,
                texto: mensaje.texto
            }
            this.mensajes.push(nuevoMensaje)
        }
  },
  mounted() {
    this.getPerson(); 
  },
 
    created() {
        console.log(this.usuario);
    },

};
</script>

<style>
body{
  background-image: url(/public/img/fondo.jpg);
}
h1{
  font-family: 'Bison', sans-serif;
  font-size: 60px;
  color: aquamarine;
}
</style>