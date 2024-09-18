<template>
  <div class="greetings-container">
    <h2>Saludos en Kichwa</h2>
    <ul>
      <li><strong>¡Ali tutamanda!</strong> / ¡Buenos días! (justo en la mañana – ¡Buena mañana!)</li>
      <li><strong>¡Ali pundza!</strong> / ¡Buenos días!</li>
      <li><strong>¡Ali chishi!</strong> / ¡Buenas tardes!</li>
      <li><strong>¡Ali tuta!</strong> / ¡Buenas noches!</li>
      <li><strong>¿Kawsangichu?</strong> / Hola, ¿cómo estás? (¿Estás vivo/a?)</li>
      <li><strong>Kawsanimi</strong> / Hola, estoy bien (Estoy vivo/a)</li>
      <li><strong>¿Kawsangichichu?</strong> / Hola, ¿cómo están uds.? (¿Están vivos/as uds.?)</li>
      <li><strong>Kawsanchimi</strong> / Hola, estamos bien (Estamos vivos/as)</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Greetings',
};
</script>

<style scoped>
.greetings-container {
  padding: 20px;
  font-family: Arial, sans-serif;
}

.greetings-container h2 {
  font-size: 1.8em;
  margin-bottom: 15px;
  text-align: center;
}

.greetings-container ul {
  list-style-type: none;
  padding: 0;
}

.greetings-container li {
  font-size: 1.2em;
  margin: 10px 0;
}

/* Responsividad */
@media (max-width: 768px) {
  .greetings-container h2 {
    font-size: 1.5em;
  }

  .greetings-container li {
    font-size: 1em;
  }
}

@media (max-width: 480px) {
  .greetings-container h2 {
    font-size: 1.3em;
  }

  .greetings-container li {
    font-size: 0.9em;
  }
}
</style>
