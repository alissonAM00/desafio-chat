<template>
  <div id="chatuser" class="container text-white">
    <div  v-for="(mensaje, index) in mensajes" :key="index">
      <p  
        :style="{
          textAlign: mensaje.id === usuarios[0].id.value ? 'left' : 'right',
        }"
      >
        <small>{{ mensaje.nombreCompleto }}</small>
      </p>
      <p  class="chatBubble "
        :style="{
          backgroundColor: mensaje.color,
          textAlign: mensaje.id === usuarios[0].id.value ? 'left' : 'right',
          
        }"
      >
        {{ mensaje.texto }}
      </p>
    </div>
  </div>
</template>

<script>

export default {
  name: "ChatUser",
  props: {
    mensajes: Array,
    usuarios: Array,
  },
  

};
</script>

<style scoped>
#chatuser {
  height: 80vh;
  overflow-y: scroll;
  background-image: url(../../public/img/chatbox.jpg);
}
.chatBubble {
  margin-bottom: 10px;
  padding: 10px;
  border-radius: 50px;
  font-family: 'Melodya Chatrina Italic', sans-serif;
  font-size: 30px;

 
  

}
</style>