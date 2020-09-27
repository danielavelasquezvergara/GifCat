<template>
  <div class="Principal">
    <div class="titulo__principal">
      <h1>RANDOM GIF CAT</h1>
    </div>

    
    <div class="Filtros">
     
      <p class="filtro__datos">
        Titulo:
        <input v-model="title" type="text" placeholder="Gatito" />
      </p>
      <p class="filtro__datos">
        Filtro:
        <select v-model="filtro_seleccionado">
          <option disabled selected> Selecciona </option>
          <option
            @click="filtro_seleccionado = elemento"
            v-for="elemento in filtros"
            :key="elemento"
            :value="elemento"
          >
            {{ elemento }}
          </option>
        </select>
      </p>
      <!-- Color de letra  -->
      <div class="filtro__datos">
        <p class="color">
          Color:
          <select v-model="color_seleccionado">
            <option disabled selected> Selecciona </option>
            <option
              @click="color_seleccionado = elemento"
              v-for="elemento in colores"
              :key="elemento"
              :value="elemento"
            >
              {{ elemento }}
            </option>
          </select>
        </p>
        <!-- color a la imagen -->
        <div
          :style="{ 'background-color': this.color_seleccionado }"
          class="circulo"
        ></div>
      </div>
      <!-- Tamaño para letra -->
      <p class="filtro__datos">
        Tamaño:
        <input v-model.number="size" type="number" min="1" />
      </p>
    </div>
  
    <div class="gif">
      <!--boton para obtener-->
      <button @click="mostrar_gato" class="boton_obtener">
        Obtener Gatito :)
      </button>
      <!-- imagen gif -->
      <div>
        <img
          v-if="image_fuente"
          :src="image_fuente"
          alt="Gato_Fail_Img_Try_Again"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      title: "", 
      filtros: ["blur", "mono", "sepia", "negative", "paint", "pixel"], 
      colores: ["red", "green", "yellow", "blue", "black", "gray"], 
      filtro_seleccionado: "Selecciona", 
      color_seleccionado: "Selecciona", 
      size: null, 
      image_fuente: "", 
    };
  },
  methods: {
    
    mostrar_gato() {
      this.image_fuente = `https://cataas.com/cat/gif/says/${this.title}?filter=${this.filtro_seleccionado}&color=${this.color_seleccionado}&size=${this.size}`;
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: 'Roboto Condensed', sans-serif;
}

.titulo__principal {
  text-align: center;
  padding: 40px;
  background-color: #7165dd;
  color: #1c3c57;
  font-weight: bold;
  font-size: 20px;
 
}

.Filtros {
  padding: 30px;
  background-color: #b64e8ade;
}

.filtro__datos{
  margin: 20px 0;
  text-align: center;
  padding-left: 45px;
  color: #394854;
  font-size: 25px;
  font-weight: bold;
}
.color {
  display: inline-block;
  align-items: center;
  margin: 30px;
  padding: 20px;
}

.circulo {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  margin-left: 40px;
  display: inline-block;
}

.gif {
  padding: 20px 0 50px 0;
  background-color:  #7165dd;
  text-align: center;
}

.boton_obtener {
  margin: 25px;
  font-size: 40px;
  border-radius: 10px;
  border-color: rgba(1, 1, 204, 0.418);
  cursor: pointer;
  background-color: #b64e8ade;
  color: #1c3c57;
}
</style>
