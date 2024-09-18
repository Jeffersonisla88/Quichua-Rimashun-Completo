<template>
  <div class="completa-frase">
    <h2>Completa la Frase</h2>
    <p>{{ fraseConEspacio }}</p>

    <div class="opciones">
      <button v-for="(opcion, index) in opciones" :key="index" @click="verificarRespuesta(opcion)">
        {{ opcion }}
      </button>
    </div>

    <p v-if="resultado !== null">{{ resultado }}</p>

    <p>Puntuación: {{ puntuacion }}</p>

    <button v-if="testCompletado" @click="cerrarTest">Finalizar Test</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      preguntas: [
        {
          frase: "El cielo es muy [espacio] durante el día.",
          palabraCorrecta: "azul",
          opciones: ["rojo", "verde", "azul", "amarillo"]
        },
        {
          frase: "¡Ali tutamanda! / ¡Buenos [espacio]!",
          palabraCorrecta: "días",
          opciones: ["noches", "días", "tardes", "mañanas"]
        },
        {
          frase: "Yo = [espacio]",
          palabraCorrecta: "Ñuka",
          opciones: ["Kan", "Pay", "Ñuka", "Ñukanchi"]
        },
        {
          frase: "Lunes en Kichwa es [espacio]",
          palabraCorrecta: "Awaki",
          opciones: ["Awaki", "Panchi", "Wacha", "Chillay"]
        }
        // Puedes agregar más preguntas aquí.
      ],
      preguntaActual: 0,
      resultado: null,
      puntuacion: 0,
      testCompletado: false
    };
  },
  computed: {
    fraseConEspacio() {
      return this.preguntas[this.preguntaActual].frase.replace("[espacio]", "_____");
    },
    opciones() {
      return this.preguntas[this.preguntaActual].opciones;
    }
  },
  methods: {
    verificarRespuesta(opcion) {
      const pregunta = this.preguntas[this.preguntaActual];
      if (opcion === pregunta.palabraCorrecta) {
        this.resultado = "¡Correcto!";
        this.puntuacion++;
      } else {
        this.resultado = "Incorrecto, inténtalo de nuevo.";
      }
      this.siguientePregunta();
    },
    siguientePregunta() {
      if (this.preguntaActual < this.preguntas.length - 1) {
        this.preguntaActual++;
        this.resultado = null;
      } else {
        this.testCompletado = true;
      }
    },
    cerrarTest() {
      alert(`¡Test finalizado! Puntuación final: ${this.puntuacion}/${this.preguntas.length}`);
      this.reiniciarTest();
    },
    reiniciarTest() {
      this.preguntaActual = 0;
      this.puntuacion = 0;
      this.testCompletado = false;
      this.resultado = null;
    }
  }
};
</script>

<style scoped>
.completa-frase {
  text-align: center;
  padding: 20px;
}

.opciones button {
  margin: 5px;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  background-color: #90ee90;
  color: #fff;
  cursor: pointer;
}

.opciones button:hover {
  background-color: #76c7c0;
}

@media (max-width: 768px) {
  .opciones button {
    font-size: 14px;
  }
}
</style>
