<template>
    <div class="questions-container">
      <h2>Preguntas en Kichwa</h2>
      <ul>
        <li><strong>¿Ima shuti angi?</strong> / ¿Cuál es tu nombre?</li>
        <li><strong>Ñuka shuti ...</strong> / Mi nombre es …</li>
        <li><strong>¿Maymanda angi?</strong> / ¿De dónde eres?</li>
        <li><strong>Ñuka …manda animi</strong> / Soy de …</li>
        <li><strong>Ñuka Ecuadormanda animi</strong> / Soy de Ecuador</li>
        <li><strong>¿Kanga?</strong> / ¿Y tú/ud.?</li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: 'Questions',
  };
  </script>
  
  <style scoped>
  .questions-container {
    padding: 20px;
    font-family: Arial, sans-serif;
  }
  
  .questions-container h2 {
    font-size: 1.8em;
    margin-bottom: 15px;
    text-align: center;
  }
  
  .questions-container ul {
    list-style-type: none;
    padding: 0;
  }
  
  .questions-container li {
    font-size: 1.2em;
    margin: 10px 0;
  }
  
  /* Responsividad */
  @media (max-width: 768px) {
    .questions-container h2 {
      font-size: 1.5em;
    }
  
    .questions-container li {
      font-size: 1em;
    }
  }
  
  @media (max-width: 480px) {
    .questions-container h2 {
      font-size: 1.3em;
    }
  
    .questions-container li {
      font-size: 0.9em;
    }
  }
  </style>
  