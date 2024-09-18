<template>
    <div class="pronouns-container">
      <h2>Pronombres en Kichwa</h2>
      
      <div class="section">
        <h3>Pronombres Personales</h3>
        <ul>
          <li><strong>Yo</strong> = Ñuka</li>
          <li><strong>Tú/usted</strong> = Kan</li>
          <li><strong>Él/ella</strong> = Pay</li>
          <li><strong>Nosotros</strong> = Ñukanchi</li>
          <li><strong>Ustedes/vosotros</strong> = Kanguna</li>
          <li><strong>Ellos</strong> = Payguna</li>
        </ul>
      </div>
  
      <div class="section">
        <h3>Pronombres Posesivos</h3>
        <ul>
          <li><strong>Mama</strong> / madre</li>
          <li><strong>Ñuka mama</strong> / mi madre</li>
          <li><strong>Kanba mama</strong> / tu madre</li>
          <li><strong>Payba mama</strong> / su madre</li>
          <li><strong>Ñukanchi mama</strong> / nuestra madre</li>
          <li><strong>Kanguna(wa) mama</strong> / su madre (de ustedes)</li>
          <li><strong>Payguna(wa) mama</strong> / su madre (de ellos)</li>
        </ul>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'Pronouns',
  };
  </script>
  
  <style scoped>
  .pronouns-container {
    padding: 20px;
    font-family: Arial, sans-serif;
  }
  
  .pronouns-container h2 {
    font-size: 1.8em;
    margin-bottom: 20px;
    text-align: center;
  }
  
  .section {
    margin-bottom: 20px;
  }
  
  .section h3 {
    font-size: 1.5em;
    margin-bottom: 10px;
    text-decoration: underline;
  }
  
  .section ul {
    list-style-type: none;
    padding: 0;
  }
  
  .section li {
    font-size: 1.2em;
    margin: 8px 0;
  }
  
  /* Responsividad */
  @media (max-width: 768px) {
    .pronouns-container h2 {
      font-size: 1.5em;
    }
  
    .section h3 {
      font-size: 1.3em;
    }
  
    .section li {
      font-size: 1em;
    }
  }
  
  @media (max-width: 480px) {
    .pronouns-container h2 {
      font-size: 1.3em;
    }
  
    .section h3 {
      font-size: 1.1em;
    }
  
    .section li {
      font-size: 0.9em;
    }
  }
  </style>
  