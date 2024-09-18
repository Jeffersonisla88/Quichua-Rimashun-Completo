<template>
    <section class="kichwa-history">
      <h1 class="title">La Historia de los Pueblos Kichwa</h1>
  
      <section class="timeline">
        <div class="timeline-item" v-for="(event, index) in timelineEvents" :key="index">
          <h2 class="event-title">{{ event.title }}</h2>
          <p class="event-description">{{ event.description }}</p>
          <img :src="event.image" alt="Imagen del evento" class="event-image">
        </div>
      </section>
    </section>
  </template>
  
  <script>
  export default {
    data() {
      return {
        timelineEvents: [
          {
            title: 'Los Primeros Kichwa',
            description: 'Los antepasados de los Kichwa, conocidos como los Quitu, se establecieron en la región central de los Andes ecuatorianos hace aproximadamente 2.000 años. Desarrollaron una sofisticada civilización...',
            image: 'path/to/image1.jpg'
          },
          // ... otros eventos de la línea de tiempo
        ]
      }
    }
  }
  </script>
  
  <style>
  .kichwa-history {
    padding: 2rem;
    background-color: #f5f5f5;
  }
  
  .title {
    text-align: center;
    font-size: 2rem;
    margin-bottom: 2rem;
  }
  
  .timeline {
    display: flex;
    flex-direction: column;
    gap: 2rem;
  }
  
  .timeline-item {
    background-color: #fff;
    border-radius: 10px;
    padding: 2rem;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    position: relative;
  }
  
  .event-title {
    font-size: 1.5rem;
    margin-bottom: 1rem;
  }
  
  .event-description {
    line-height: 1.5;
  }
  
  .event-image {
    width: 100%;
    height: auto;
    margin-top: 1rem;
    border-radius: 5px;
  }
  
  /* Estilos adicionales para personalizar la apariencia */
  </style>