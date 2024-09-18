<template>
  <div class="container">
    <div class="header">
      <div class="title">INICIO</div>
      <div class="time">10:42</div>
    </div>
    
    <!-- Medidor de progreso -->
    <progress-meter :progress="progress"></progress-meter>

    <!-- Lista de lecciones -->
    <div class="lessons">
      <div class="lesson" v-for="(lesson, index) in lessons" :key="index">
        <div class="lesson-title">{{ lesson.title }}</div>
        <div class="lesson-content">
          <img :src="lesson.image" alt="Lesson Image" />
          <div class="lesson-description">{{ lesson.description }}</div>
        </div>
        <div class="lesson-button">
          <button
            :class="lesson.locked ? 'locked' : 'unlocked'"
            @click="openLesson(lesson)"
          >
            Acceso
          </button>
        </div>
      </div>
    </div>

    <!-- Modal flotante para mostrar la lección -->
    <div v-if="isLessonModalVisible" class="lesson-modal">
      <div class="lesson-modal-content">
        <button @click="closeLesson" class="close-button">&times;</button>
        <h3>{{ selectedLesson.title }}</h3>
        <component :is="getLessonComponent(selectedLesson.title)" />
        <button @click="completeLesson" class="complete-button">Finalizar Revisión</button>
      </div>
    </div>
  </div>
</template>

<script>
import ProgressMeter from "@/components/ProgressMeter.vue";
import Tema1 from "@/components/Tema1.vue";
import Tema2 from "@/components/Tema2.vue";
import Tema3 from "@/components/Tema3.vue";
import Tema4 from "@/components/Tema4.vue";
import Tema5 from "@/components/Tema5.vue";

export default {
  components: {
    ProgressMeter,
    Tema1,
    Tema2,
    Tema3,
    Tema4,
    Tema5
  },
  data() {
    return {
      lessons: [
        { title: "Lección 1", image: " @/assets/Abecedario.jpg", description: "Saludos", locked: false, component: 'Tema1' },
        { title: "Lección 2", image: "assets/Logo.jpg", description: "Respuestas a datos personales", locked: true, component: 'Tema2' },
        { title: "Lección 3", image: "/path/to/lesson3/Abecedario.png", description: "Conversaciones", locked: true, component: 'Tema3' },
        { title: "Lección 4", image: "/path/to/lesson4/image.jpg", description: "Pronombres personales", locked: true, component: 'Tema4' },
        { title: "Lección 5", image: "/path/to/lesson5/image.jpg", description: "Dias y Meses del año", locked: true, component: 'Tema5' }
      ],
      isLessonModalVisible: false,
      selectedLesson: null,
      progress: 0, // Estado para el medidor de progreso
      lessonsReviewed: 0, // Estado para llevar el conteo de las lecciones completadas
    };
  },
  methods: {
    openLesson(lesson) {
      this.selectedLesson = lesson;
      this.isLessonModalVisible = true;
    },
    closeLesson() {
      this.isLessonModalVisible = false;
      this.selectedLesson = null;
    },
    completeLesson() {
      this.lessonsReviewed += 1;
      this.updateProgress();
      this.closeLesson();
    },
    updateProgress() {
      // Calcular el progreso en función del número de lecciones revisadas
      const totalLessons = this.lessons.length;
      this.progress = Math.min(100, (this.lessonsReviewed / totalLessons) * 100);
    },
    getLessonComponent(title) {
      const lesson = this.lessons.find(l => l.title === title);
      return lesson ? lesson.component : null;
    }
  }
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  height: 100vh;
  background-color: #d1c4e9;
  padding: 20px;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}

.title {
  font-size: 24px;
  font-weight: bold;
}

.time {
  font-size: 16px;
  color: #666;
}

/* Medidor de progreso */
.progress-container {
  margin-bottom: 20px;
  background-color: #e0e0e0;
  border-radius: 15px;
  position: relative;
  height: 30px;
  width: 100%;
}

.progress-bar {
  height: 100%;
  background-color: #76c7c0;
  border-radius: 15px 0 0 15px;
  transition: width 0.4s ease;
}

.progress-text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: #fff;
  font-weight: bold;
  font-size: 16px;
}

/* Estilo de las lecciones */
.lessons {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.lesson {
  background-color: #fff;
  border-radius: 10px;
  padding: 20px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.lesson-title {
  font-size: 20px;
  font-weight: bold;
  margin-bottom: 10px;
}

.lesson-content {
  display: flex;
  align-items: center;
  gap: 20px;
  margin-bottom: 10px;
}

.lesson-content img {
  width: 100px;
  height: 100px;
  object-fit: cover;
  border-radius: 5px;
}

.lesson-description {
  font-size: 16px;
}

.lesson-button {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.locked,
.unlocked {
  padding: 10px 20px;
  border-radius: 5px;
  border: none;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
}

.locked {
  background-color: #f08080;
  color: #fff;
}

.unlocked {
  background-color: #90ee90;
  color: #fff;
}

/* Modal flotante */
.lesson-modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
}

.lesson-modal-content {
  background-color: white;
  padding: 30px;
  border-radius: 10px;
  text-align: center;
  width: 80%;
  max-width: 500px;
  position: relative;
}

.close-button {
  position: absolute;
  top: 10px;
  right: 10px;
  background: none;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
}

.complete-button {
  margin-top: 20px;
  padding: 10px 20px;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
</style>
