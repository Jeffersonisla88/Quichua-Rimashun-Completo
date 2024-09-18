<template>
    <div class="calendar-container">
      <div class="scrollable-table">
        <table class="calendar-table">
          <thead>
            <tr>
              <th>Kichwa</th>
              <th>Español</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td colspan="2" class="section-title">Hunkay Punchákuna / Días de la Semana</td>
            </tr>
            <tr v-for="(day, index) in days" :key="index">
              <td>{{ day.kichwa }}</td>
              <td>{{ day.spanish }}</td>
            </tr>
            <tr>
              <td colspan="2" class="section-title">Wata Killakuna / Meses del Año</td>
            </tr>
            <tr v-for="(month, index) in months" :key="index">
              <td>{{ month.kichwa }}</td>
              <td>{{ month.spanish }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        days: [
          { kichwa: 'Awaki', spanish: 'Lunes' },
          { kichwa: 'Awkarik', spanish: 'Martes' },
          { kichwa: 'Chillay', spanish: 'Miercoles' },
          { kichwa: 'Kullka', spanish: 'Jueves' },
          { kichwa: 'Chaska', spanish: 'Viernes' },
          { kichwa: 'Wacha', spanish: 'Sabado' },
          { kichwa: 'Inti', spanish: 'Domingo' },
        ],
        months: [
          { kichwa: 'Kulla', spanish: 'Enero' },
          { kichwa: 'Panchi', spanish: 'Febrero' },
          { kichwa: 'Pawkar', spanish: 'Marzo' },
          { kichwa: 'Ayriwa', spanish: 'Abril' },
          { kichwa: 'Aymuray', spanish: 'Mayo' },
          { kichwa: 'Raymi', spanish: 'Junio' },
          { kichwa: 'Sitwa', spanish: 'Julio' },
          { kichwa: 'Karway', spanish: 'Agosto' },
          { kichwa: 'Kuski', spanish: 'Septiembre' },
          { kichwa: 'Wayru', spanish: 'Octubre' },
          { kichwa: 'Sasi', spanish: 'Noviembre' },
          { kichwa: 'Kapak', spanish: 'Diciembre' },
        ],
      };
    },
  };
  </script>
  
  <style scoped>
  .calendar-container {
    margin: 20px;
    background-color: #f0f0f0;
    padding: 20px;
    border-radius: 10px;
  }
  
  .scrollable-table {
    max-height: 300px; /* Altura máxima del contenedor */
    overflow-y: auto; /* Habilitar scroll vertical */
  }
  
  .calendar-table {
    width: 100%;
    border-collapse: collapse;
  }
  
  .calendar-table th,
  .calendar-table td {
    border: 1px solid #ddd;
    padding: 8px;
    text-align: left;
  }
  
  .calendar-table th {
    background-color: #f2f2f2;
  }
  
  .section-title {
    font-weight: bold;
    text-align: center;
  }
  
  /* Responsividad */
  @media (max-width: 768px) {
    .calendar-table {
      font-size: 14px;
    }
  }
  
  .scrollable-table::-webkit-scrollbar {
    width: 10px; /* Tamaño del scrollbar */
  }
  
  .scrollable-table::-webkit-scrollbar-thumb {
    background-color: #888; /* Color del cursor */
    border-radius: 5px; /* Bordes redondeados */
  }
  
  .scrollable-table::-webkit-scrollbar-thumb:hover {
    background-color: #555; /* Color del cursor al pasar el mouse */
  }
  </style>
  