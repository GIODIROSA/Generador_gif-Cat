<template>
  <div id="app">
    <!-- titulo -->

    <div class="title">
      <h1 class="title_principal">Random Gif Cat</h1>
      <label class="title_msg">Escribe un Mensaje: </label>
      <input
        v-model.trim="mensaje"
        type="text"
        placeholder="mensaje"
        class="msgTitleCat"
      />
    </div>

    <!-- filtro -->

    <div class="filter_cat">
      <label class="title_filtro">Filtro: </label>
      <select v-model="filtroSelect" class="optionfilter">
        <option disabled selected>Seleccione un Filtro</option>
        <option
          @click="filtroSelect = item"
          v-for="item in filter"
          :key="item.id"
          :value="item"
          >{{ item }}</option
        >
      </select>
    </div>

    <!-- color -->

    <div class="color_cat">
      <label class="title_color">Color: </label>
      <select v-model="colorSelect" class="selectorColor">
        <option disabled selected>Selecciona un color</option>
        <option
          @click="colorSelect = item"
          v-for="item in colores"
          :key="item.id"
          :value="item"
          >{{ item }}</option
        >
      </select>
      <div
        class="circulo_color"
        :style="{ 'background-color': this.colorSelect }"
      ></div>
    </div>

    <!-- tamaño -->

    <div class="sizeTextCat">
      <Label class="title_size">Tamaño: </Label>
      <input
        v-model="size"
        type="number"
        min="1"
        placeholder="400"
        class="sizecat"
      />
    </div>

    <!-- boton que genera la imagen -->

    <div class="btnCat">
      <button class="btn_obtener" @click="obtenerGato">Obtener Gatito</button>
    </div>

<!-- llamado a la api de gatos e imagen del gato -->

    <div class="contenedor_imagen">
      <img
        class="imagenGato"
        :src="imgCat"
        alt="Gift de gato aparecerá en breves minutos..."
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      filter: ["blur", "mono", "sepia", "negative", "paint", "pixel"],
      colores: ["red", "green", "yellow", "blue", "black", "gray"],
      filtroSelect: "",
      colorSelect: "",
      size: null,
      mensaje: "",
      imgCat: "",
    };
  },
  methods: {
    obtenerGato() {
      this.imgCat = `https://cataas.com/cat/says/${this.mensaje}?filter=${this.filtroSelect}&color=${this.colorSelect}&size=${this.size}`;
    }, //final obtenergato
  }, //final methods
}; // final export
</script>

<style lang="scss" scoped>
// configuracion de titulo y mensaje de la imagen de gato
.title {
  background: #3b2e5a;
  width: 550px;
  margin: auto;
  padding: 50px;
  text-align: center;
  color: white;
  .title_principal {
    font-size: 50px;
  }
  .title_msg {
    font-size: 20px;
    padding: 10px;
  }
  .msgTitleCat {
    border: 0px;
    padding: 10px;
    border-radius: 5px;
    color: #3282b8;
  }
}
// configuracion del selector de filtro
.filter_cat {
  background: #394989;
  width: 550px;
  padding: 50px;
  margin: auto;
  display: flex;
  justify-content: flex-start;
  font-size: 20px;
  color: white;

  .title_filtro {
    margin: 0 20px 0px 0px;
  }
  .optionfilter {
    padding: 10px;
    color: #3282b8;
    border-radius: 5px;
  }
}
// configuración del selector de gato
.color_cat {
  background: #fff48f;
  margin: auto;
  padding: 50px;
  width: 550px;
  display: flex;
  justify-content: space-between;
  color: #3b2e5a;
  font-size: 20px;

  .circulo_color {
    border-radius: 50%;
    width: 30px;
    height: 30px;
  }
  .selectorColor {
    padding: 10px;
    border: 0px;
    border-radius: 5px;
  }
}
// configuración del tamaño del texto que aparece en la imagen gato
.sizeTextCat {
  background: #4ea0ae;
  margin: auto;
  padding: 50px;
  width: 550px;
  display: flex;
  justify-content: flex-start;
  font-size: 20px;
  .title_size {
    margin: 0 20px 0px 0px;
  }
  .sizecat {
    padding: 10px;
    border: 0px;
    color: #3282b8;
    border-radius: 5px;
  }
}
// configuracion del btn generador de imagen gato
.btnCat {
  display: flex;
  justify-content: center;
  align-content: center;
  padding: 20px;
  .btn_obtener {
    padding: 10px;
    border: 0px;
    border-radius: 20px;
    background-color: #3b2e5a;
    color: white;
  }
}
// configuracion de imagen gato
.contenedor_imagen {
  background: #394989;
  margin: auto;
  width: 550px;
  padding: 50px;
  display: flex;
  justify-content: center;
  align-content: center;

  .imagenGato {
    width: 350px;
    height: 250px;
  }
}
</style>
