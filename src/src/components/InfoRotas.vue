<template>
  <div>
    <div class="col-sm-10">
      <!-- Rota1 -->
      <div class="card-wrapper">
        <!--Front Side-->
        <div class="face front">
          <!-- Image-->
          <div class="view overlay">
            <img class="card-img-top" src="../assets/rota1imagem.jpg" alt="Example photo" />
            <a>
              <div class="mask rgba-white-slight"></div>
            </a>
          </div>
          <!--Content-->
          <div class="card-body">
            <h4 class style="text-align:center">
              Rota 1
              <img src="../assets/circuloverde1.png" /> Baixo Corgo
            </h4>
            <p class="card-text" style="text-align:center">
              Armamar, Galafura, Lamego, Mesão Frio, Peso da Régua - Poirares,
              Peso da Régua - Vilarinho de Freires, Pinhão, Sabrosa, Santa Marta
              de Penaguião, Vila Real
            </p>
            <div style="text-align:right">
              <button class="btn btn-simple" id="1" @click="seleteRoute(1)">
                <i class="fa fa-mail-forward"></i>
                <router-link to="/routesdescription">Ver mais</router-link>
              </button>
            </div>
          </div>
        </div>
      </div>
      <br />
      <!-- Rota2 -->
      <div class="card-wrapper">
        <!--Front Side-->
        <div class="face front">
          <!-- Image-->
          <div class="view overlay">
            <img class="card-img-top" src="../assets/rota2imagem.jpg" alt="Example photo" />
            <a>
              <div class="mask rgba-white-slight"></div>
            </a>
          </div>
          <!--Content-->

          <div class="card-body">
            <h4 class style="text-align:center">
              Rota 2
              <img src="../assets/circuloroxo1.png" /> Alto corgo
            </h4>
            <p class="card-text" style="text-align:center">
              Figueira de Castelo Rodrigo, Freixo de Espada à Cinta, Pinhão,
              Torre de Moncorvo, >Vila Flor, Vila Nova de Foz Côa, Carrazeda de
              Ansiães, Mêda
            </p>
          </div>
          <div style="text-align:right" id="2" @click="seleteRoute(2)">
            <button class="btn btn-simple">
              <i class="fa fa-mail-forward"></i>
              <router-link to="/routesdescription">Ver mais</router-link>
            </button>
          </div>
        </div>
      </div>

      <br />
      <!-- Rota3 -->
      <div class="card-wrapper">
        <!--Front Side-->
        <div class="face front">
          <!-- Image-->
          <div class="view overlay">
            <img class="card-img-top" src="../assets/rota3imagem.jpg" alt="Example photo" />
            <a>
              <div class="mask rgba-white-slight"></div>
            </a>
          </div>

          <!--Content-->
          <div class="card-body">
            <h4 class style="text-align:center ">
              Rota 3
              <img src="../assets/circulovermelho1.png" /> À descoberta do
              Douro Superior
            </h4>
            <p class="card-text" style="text-align:center">
              Armamar, Galafura, Lamego, Mesão Frio, Peso da Régua - Poirares,
              Peso da Régua - Vilarinho de Freires, Pinhão, Sabrosa, Santa Marta
              de Penaguião, Vila Real
            </p>

            <div style="text-align:right">
              <button class="btn btn-simple" id="3" @click="seleteRoute(3)">
                <i class="fa fa-mail-forward"></i>
                <router-link to="/routesdescription">Ver mais</router-link>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  methods: {
    addWineries() {
      this.$store.commit("ADD_WINERIES");
    },
    seleteRoute(id) {
      this.$store.commit("SELECT_ROUTE", {
        idRoute: id
      });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#seeWineries {
  align-self: center;
  background-color: white;
  color: black;
}

h5,
h4 {
  font-family: "Didact Gothic", sans-serif;
}

@import url("https://fonts.googleapis.com/css?family=Cinzel&display=swap");

@import url("https://fonts.googleapis.com/css?family=Didact+Gothic&display=swap");
</style>
