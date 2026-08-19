<script setup>
import { ref } from 'vue'

const nombre = ref('')
const apellido = ref('')
const nacimiento = ref('')
const genero = ref('')
const telefono = ref ('')
const pais = ref('')
const ciudad = ref('')
const postal = ref('')
const carrera = ref('')


const estudiantes = ref([])

function agregarEstudiante() {
  if (!nombre.value || !apellido.value || !nacimiento.value || !genero.value || !telefono.value || !pais.value || !ciudad.value || !postal.value ||!carrera.value) {
    alert('Por favor, complete todos los campos.')
    return
  }

  estudiantes.value.push({
    nombre: nombre.value,
    apellido: apellido.value,
    nacimiento: nacimiento.value,
    genero: genero.value,
    telefono : telefono.value,
    pais: pais.value,
    ciudad: ciudad.value,
    postal : postal.value,
    carrera: carrera.value
  })

  nombre.value = ''
  apellido.value = ''
  nacimiento.value = ''
  genero.value = ''
  telefono.value =''
  pais.value = ''
  ciudad.value = ''
  postal.value = ''
  carrera.value = ''
}
</script>

<template>
  <div class="contenedor">

    <h1>Formulario de Admision</h1>

    <form @submit.prevent="agregarEstudiante">

      <div class="campo">
        <label>Nombre</label>
        <input
          type="text"
          v-model="nombre"
          placeholder="Ingrese su nombre"
        >
      </div>

      <div class="campo">
        <label>Apellido</label>
        <input type="text" v-model="apellido" placeholder="Ingrese su apellido"
        >
      </div>

      <div class="campo">
        <label >Nacimiento</label>
        <input type="text" v-model="nacimiento" placeholder="Introduzca su fecha de Nacimiento">
      </div>

      <div class="campo">
        <label>Género</label>

        <div class="radios">
          <label>
            <input type="radio" value="Masculino" v-model="genero"> Masculino
          </label>

          <label>
            <input type="radio"  value="Femenino" v-model="genero" >
            Femenino
          </label>
          <label>
            <input type="radio" value="Otro" v-model="genero">
            Otro
          </label>
        </div>

        <div class="campo">
          <label > Telefono </label>
          <input type="text" v-model="telefono" placeholder="Introduzca Telefono/Celular">
        </div>

        <div class="campo">
        <label >Pais</label>
        <input type="text" v-model="pais" placeholder="Pais">
        </div>

        <div class="campo">
        <label for="">Ciudad</label>
        <input type="text" v-model="ciudad" placeholder="Ciudad">
        </div>

        <div class="campo">
        <label  >Codigo Postal</label>
        <input type="text" v-model="postal" placeholder="Codigo Postal">
        </div>
      </div>

      <div class="campo">
        <label>Carreras Disponibles</label>

        <select v-model="carrera">
          <option value="">Seleccione una carrera</option>
          <option>Ingeniería de Software</option>
          <option>Ingeniería en Sistemas</option>
          <option>Administración de Empresas</option>
          <option>Contabilidad</option>
          <option>Derecho</option>
          <option>Educación</option>
        </select>
      </div>

      <button type="submit">
        Agregar estudiante
      </button>

    </form>

    <div v-if="estudiantes.length > 0" class="tabla-container">

      <h2>Estudiantes Ingresados</h2>

      <table>
        <thead>
          <tr>
            <th>#</th>
            <th>Nombre</th>
            <th>Apellido</th>
            <th>Nacimiento</th>
            <th>Género</th>
            <th>Telefono</th>
            <th>Pais</th>
            <Th>Ciudad</Th>
            <th> Postal</th>
            <th>Carrera</th>
          </tr>
        </thead>

        <tbody>
          <tr
            v-for="(estudiante, index) in estudiantes"
            :key="index"
          >
            <td>{{ index + 1 }}</td>
            <td>{{ estudiante.nombre }}</td>
            <td>{{ estudiante.apellido }}</td>
            <td>{{ estudiante.nacimiento }}</td>
            <td>{{ estudiante.genero }}</td>
            <td>{{ estudiante.telefono }}</td>
            <td>{{ estudiante.pais }}</td>
            <td>{{ estudiante.ciudad }}</td>
            <td>{{ estudiante.postal }}</td>
            <td>{{ estudiante.carrera }}</td>
          
          </tr>
        </tbody>
      </table>

    </div>

    <p v-else class="mensaje">
      No hay estudiantes registrados.
    </p>

  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: Arial, sans-serif;
  background: #f2f5f7;
}

.contenedor {
  width: 80%;
  max-width: 900px;
  margin: 40px auto;
  background: white;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
  margin-top: 80px;
}

h1 {
  text-align: center;
  margin-bottom: 30px;
  color: #080736;
  font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif ;
}

.campo {
  margin-bottom: 18px;
}

.campo label {
  display: block;
  margin-bottom: 7px;
  font-weight: bold;
}

input[type="text"],
select {
  width: 100%;
  padding: 11px;
  border: 1px solid #ccc;
  border-radius: 6px;
  font-size: 15px;
}

.radios {
  display: flex;
  gap: 20px;
}

.radios label {
  font-weight: normal;
}

button {
  width: 100%;
  padding: 12px;
  border: none;
  border-radius: 6px;
  background: #1b6e6e;
  color: white;
  font-size: 16px;
  cursor: pointer;
}

button:hover {
  background: #145252;
}

.tabla-container {
  margin-top: 35px;
}

h2 {
  margin-bottom: 15px;
  color: #333;
}

table {
  width: 50%;
  border-collapse: collapse;
}

th,
td {
  padding: 12px;
  border: 1px solid #ddd;
  text-align: left;
 
}

th {
  background: #1b6e6e;
  color: white;
}

tr:nth-child(even) {
  background: #f5f5f5;
}

.mensaje {
  text-align: center;
  margin-top: 30px;
  color: #777;
}

@media (max-width: 600px) {
  .contenedor {
    width: 95%;
    padding: 20px;
  }

  table {
    font-size: 13px;
  }

  th,
  td {
    padding: 8px;
  }
}
</style>