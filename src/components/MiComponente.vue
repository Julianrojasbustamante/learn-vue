<template>
  <div>
    <h1>{{ text }}</h1>
    <h2>Los productos son:</h2>
    <div v-for="product in productos">
      <p>{{product.nombre}}</p>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "MiComponente",
  data(){
    return {
      text: "Esto es un nuevo componente",
      producto: {
        descripcion: "",
        estado: 1,
        id: 1,
        imagenPrincipal: "",
        imagenes: [""],
        nombre: "",
        precio: 1,
        unidadesDisponibles: 1
      },
      productos: []
    }
  },
  created() {
    axios.get("https://celuphone-b12a9-default-rtdb.firebaseio.com/datos.json").then((result) => {
      console.log(result.data);
      this.productos = result.data;
    })
  },
  methods:{
  }
}
</script>