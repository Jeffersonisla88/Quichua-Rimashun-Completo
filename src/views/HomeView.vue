<template>
  <div class="home">
    <div class="overlay"></div>
    <div class="content">
      <!-- Mostrar el mensaje de bienvenida si existe -->
      <div v-if="welcomeMessage" class="welcome-message">
        <h2>{{ welcomeMessage }}</h2>
        <p>Esperamos que disfrutes de nuestra aplicación.</p>
      </div>

      <!-- Mostrar el contenido inicial si no hay mensaje de bienvenida -->
      <div v-else>
        <h2 class="animated-text">Comienza tu aventura en el mundo del quichua</h2>
        <p>Descubre juegos, canciones y muchas sorpresas mientras aprendes.</p>
        <button @click="showLogin" class="cta-button">¡Empezar ahora!</button>
      </div>
    </div>

    <!-- Modal flotante para el login -->
    <div v-if="isLoginVisible" class="login-modal">
      <div class="login-content">
        <button @click="hideLogin" class="close-button">&times;</button>
        <h3>Únete para empezar tu aventura</h3>
        <p>Regístrate para desbloquear contenido exclusivo y comenzar tu aprendizaje en quichua.</p>
        <input
          type="text"
          v-model="name"
          placeholder="Ingresa tu nombre"
          class="input-field"
        />
        <button @click="login" class="login-button">Iniciar sesión</button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import backgroundImage from "@/assets/logo.png"; // Importa la imagen

export default defineComponent({
  name: "Home",
  data() {
    return {
      backgroundImage,
      isLoginVisible: false, // Controla la visibilidad del modal
      name: "", // Almacena el nombre del usuario
      welcomeMessage: "", // Almacena el mensaje de bienvenida
    };
  },
  methods: {
    showLogin() {
      this.isLoginVisible = true;
    },
    hideLogin() {
      this.isLoginVisible = false;
    },
    login() {
      if (this.name.trim()) {
        // Guardar el nombre del usuario en localStorage
        localStorage.setItem("userName", this.name);

        // Ocultar el modal de login
        this.isLoginVisible = false;

        // Mostrar el mensaje de bienvenida
        this.welcomeMessage = `Muchas gracias por iniciar sesión con nosotros, ${this.name}. Esperamos que disfrutes de nuestra app.`;
      } else {
        alert("Por favor, ingresa tu nombre");
      }
    },
  },
});
</script>

<style scoped>
/* Fondo con imagen */
.home {
  position: relative;
  background-image: url('@/assets/logo.png');
  background-size: cover;
  background-position: center;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  padding: 20px;
  color: #fff;
  overflow: hidden;
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.6));
  z-index: 1;
  opacity: 0.8;
}

.content {
  position: relative;
  z-index: 2;
  background-color: rgba(0, 0, 0, 0.5);
  padding: 30px;
  border-radius: 15px;
  max-width: 600px;
  animation: fadeIn 1.5s ease-in-out;
}

.cta-button {
  background-color: #f39c12;
  color: white;
  padding: 15px 30px;
  border: none;
  border-radius: 25px;
  font-size: 1.2em;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.cta-button:hover {
  background-color: #e67e22;
  transform: scale(1.05);
}

/* Mensaje de bienvenida */
.welcome-message {
  color: #42b983;
}

/* Fondo del modal con desenfoque */
.login-modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.7);
  backdrop-filter: blur(8px); /* Desenfoque del fondo */
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

/* Contenedor del contenido del login */
.login-content {
  background-color: #fff;
  padding: 40px;
  border-radius: 20px;
  width: 100%;
  max-width: 400px;
  box-shadow: 0px 10px 30px rgba(0, 0, 0, 0.2);
  text-align: center;
  position: relative;
  animation: fadeIn 0.5s ease-in-out;
}

/* Botón para cerrar el modal */
.close-button {
  background: none;
  border: none;
  font-size: 1.5rem;
  color: #333;
  position: absolute;
  top: 15px;
  right: 15px;
  cursor: pointer;
  transition: transform 0.3s ease;
}

.close-button:hover {
  transform: scale(1.2);
}

/* Título elegante */
h3 {
  font-size: 1.8rem;
  margin-bottom: 10px;
  color: #333;
}

/* Descripción */
p {
  font-size: 1rem;
  color: #666;
  margin-bottom: 20px;
}

/* Estilo de campo de entrada */
.input-field {
  width: 100%;
  padding: 15px;
  margin-bottom: 20px;
  border: 2px solid #ddd;
  border-radius: 8px;
  font-size: 1rem;
  color: #333;
  box-sizing: border-box;
  transition: border-color 0.3s ease;
}

.input-field:focus {
  outline: none;
  border-color: #42b983;
}

/* Botón de iniciar sesión */
.login-button {
  background-color: #42b983;
  color: #fff;
  border: none;
  padding: 15px;
  width: 100%;
  border-radius: 8px;
  font-size: 1.2rem;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.login-button:hover {
  background-color: #39a87f;
  transform: scale(1.05);
}

/* Animación de entrada */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(-20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
