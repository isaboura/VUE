<script setup>
import { ref, computed } from "vue";

const nombre = "Ismail";
const color = "color : red";

const esMartes = null ;

const dias = ["Luenes", "Martes", "Miercoles", "Jueves"];

const activo = true;

const arrayfrutas = ["Pera", "manzana", "uva", "melocoton"];


const arraydeFrutas = [
   {
    name: "Manzana",
    price: "3.00€",
    descripcion: "Manzana Golden",
    stock: 0
  },
  {
    name: "Platano",
    price: "4.00€",
    descripcion: "Platano canarias",
    stock: 2
  },
  {
    name: "Naranza",
    price: "6.00€",
    descripcion: "Naranja Zumo",
    stock: 10
  }
];

const objetoFruta = {
  name: "Naranza",
  price: "6.00€",
  descripcion: "Naranja Zumo"
};


const hacerClick = (mensaje) => {
  console.log("mensaje")
};

const arrayFavoritos = ref([]);
const contar = ref(0);
const contador = computed(() => {
  if (contar.value == 0) {
    return "zero";
  }
  return contar.value > 0 ? "verde" : "rojo";
});

const bloquearBoton = computed(() => {
  if (arrayFavoritos.value.find((numero1) => numero1 === contar.value)) return true;
  if (contar.value == 0) return true;

  return false;
})

const sumar = () => {
  contar.value ++;
  console.log(contar)
};

const restar = ()  => {
  contar.value --;
  console.log(contar)
}

const resetera  = () => {
  contar.value = 0;
  console.log(contar)
}

const añadir = () => {
  arrayFavoritos.value.push(contar.value)
}
</script>
<template>
<!-- Colores y nombre -->
<h2 :style="color">Hola {{ nombre.toLowerCase() }} !!</h2>

<h2>{{ esMartes ? "Hoy es martes ": "Hoy no es martes " }}</h2>
<!-- Seleccionar una cosa en concreto del array -->
<h2> Hoy es {{ dias[2] }}</h2>


<!-- If y else -->
<h2 v-if="esMartes">v-if me dice que es martes</h2>
<h2 v-if="!esMartes">v-if me dice que no es martes</h2>

<h2 v-if="esMartes">v-if me dice que es martes</h2>
<h2 v-else>else me dice que no es martes</h2>

<h2 v-if="esMartes === true">v-if me dice que es martes</h2>
<h2 v-else-if="esMartes === false"> v-else-if me dice que no es martes</h2>
<h2 v-else> v-else me dice que no es martes</h2>


<!-- Si la variable esta en true se mostrar en la pantalla si esta en false no se mostrara -->
<h2 v-show="activo"> Estoy en true</h2>

<!-- Acceder a una lista y mostrara su indice  -->
<h2>Array de frutas</h2>
 <ul>
  <li v-for="(frutas, index) in arrayfrutas" :key="index">
    {{ index }} - {{ frutas }}
  </li>
 </ul>

 <br>
 <br>
 <!-- Array y acceder al dato que queremos de ese objeto -->
<h2>Array de frutas con datos </h2>
 <ul>
  <li v-for="fruta in arraydeFrutas" :key="name">
    {{ fruta.name }} - {{ fruta.descripcion }} - {{ fruta.price }}
  </li>
 </ul>

<h2>Objetos</h2>
{{ objetoFruta.name }} - {{ objetoFruta.price }}

<ul>
  <li v-for="(index, propiedad, valor) in objetoFruta">
    {{ valor }} - {{ propiedad }} - {{ index }}
  </li>
</ul>

<!-- Hacer un for y una condicion if dentro -->
<h2>v-for y v-if</h2>
<br>
<template v-for="fruta in arraydeFrutas" :key="fruta.name">
<ul>
  <li v-if="fruta.stock > 0">
    {{ fruta.name }}
  </li>
</ul>
</template>

<h2>Botones</h2>
<!-- Botones -->
<div class="container m-3">
<button class="m-2" @click.left="hacerClick('Click en boton 1')">Click derecho</button>
<button class="m-2" @click.right.prevent="hacerClick('Click en boton 2')">Cick derecho</button>
<button class="m-2" @click.middle.prevent="hacerClick('Click en boton 3')">Click en el boton del centro</button>
</div>

<h2>Ejercicio practico1</h2>
<h3>variables reactivas</h3>
<div class="container">

<h2 :class="contador" class="m-2"> {{ contar }}</h2>

<button @click="sumar()" class="btn btn-primary m-2">Incrementar</button>
<button @click="restar()" class="btn btn-danger m-2">Restar</button>
<button @click="resetera()" class="btn btn-warning m-2">Resetear</button>
<button @click="añadir()" :disabled = "bloquearBoton" class="btn btn-success m-2"> Añadir favoritos</button>

<p class="m-2" >{{ arrayFavoritos }}</p>



</div>
</template>

<style>

</style>
