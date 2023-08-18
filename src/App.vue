<script setup>
/* interpolación de texto {{  }} */
/* v-bind o : que no nos permite la interpolación de texto, es utilizar el {{  }} en atributos*/
const arrayTitle = ["interpolacion", "v-if", "v-for", "v-if v-for", "v-on @"];
const name = "HUGO";
const lastname = "quispe";
/* v-if */
const styleColor = "color: blue";
const arrayColors = ["blue", "green", "peru"];
const active = null;
/* v-for */
const arrayFruit = ["apple", "banana", "grapes", "cherry", "watermelon"];
const arrayNames = ["Hugo", "Diego Alonso", "George", "Stephano", "Sasaki"];
const arrayFruitObj = [
  {
    name: "manzana",
    price: "$1.00",
    descripcion: "Una manzana",
    stock: 20,
  },
  {
    name: "platano",
    price: "$2.00",
    descripcion: "Una platano",
    stock: 15,
  }, {
    name: "limon",
    price: "$5.00",
    descripcion: "Una limon",
    stock: 20,
  }, {
    name: "piña",
    price: "$4.00",
    descripcion: "Una piña",
    stock: 10,
  },
];
const objetoRopa = {
  name: "casaca",
  price: "$100.00",
  descripcion: "Una casaca",
  id: 1,
};

/* v-on || methods*/
const handleClick = (message) => {
  console.log(message);
};  
</script>

<template>
  <!-- v-on - @click -->
  <h1 class="title">{{ arrayTitle[4].toLocaleUpperCase() }}</h1>
  <button v-on:click.right="handleClick('Texto Right')">Activame Right</button>
  <button @click.left="handleClick('Texto Left')">Activame Left</button>
  <button @click.middle="handleClick('Texto Middle')">Activame Middle</button>

  <!-- interpolación de texto {{  }} -->
  <h1 class="title">{{ arrayTitle[0].toLocaleUpperCase() }}</h1>
  <h1>Nombre : {{ name.toLowerCase() }}</h1>
  <h1>LastName : {{ lastname.toLocaleUpperCase() }}</h1>
  <h1>array de colores : {{ arrayColors }}</h1>
  <h2 :style="`color: ${arrayColors[2]}`">Soy Peru</h2>
  <h2 :style="`color: ${arrayColors[0]}`">soy azul</h2>
  <h2 :style="`color: ${arrayColors[1]}`">soy green</h2>
  <!-- v-if -->
  <h1 class="title">{{ arrayTitle[1].toLocaleUpperCase() }}</h1>
  <h2>
    {{ active ? "Estoy activo sin if" : "Estoy inactivo sin if" }}
  </h2>
  <h2 v-if="active === true">Estoy activo</h2>
  <h2 v-else-if="active === false">Estoy inactivo</h2>
  <h2 v-else>Estoy indesiso</h2>
  <!-- v-for -->
  <h1 class="title">{{ arrayTitle[2].toLocaleUpperCase() }}</h1>
  <!-- v-for de frutas -->
  <ul>
    <li v-for="(fruit, index) in arrayFruit" :key="index">
      {{ index }} - {{ fruit }}
    </li>
  </ul>
  <!-- v-for de nombres -->
  <ul>
    <li v-for="(name, index) in arrayNames" :key="index">
      {{ name }}
    </li>
  </ul>
  <!-- v-for challenge -->
  <ul>
    <li v-for="fruta in arrayFruitObj" :key="fruta.name">
      <h2>Fruta: {{ fruta.name }} - {{ fruta.price }} - {{ fruta.descripcion }} </h2>
    </li>
  </ul>
  <!-- v-for challenge con obj -->
  {{ objetoRopa }}
  <ul>
    <li v-for="(value, propiedad, index) in objetoRopa" :key="value">
      {{ index }} - {{ propiedad }} : {{ value }}
    </li>
  </ul>
  <!-- v-if - v-for -->
  <h1 class="title">{{ arrayTitle[3].toLocaleUpperCase() }}</h1>
  {{ arrayFruitObj }}
  <!-- solucion 1 - error 1 -->

  <!-- solucion 1 - error 1 -->
  <ul>
    <template v-for="item in arrayFruitObj" :key="item.name">
      <li v-if="item.stock === 20">
        {{ item.name }} - {{ item.price }}
      </li>
    </template>
  </ul>
</template>

<style scoped>
.title {
  text-align: center;
}
</style>