<template>
  <div class="wrapper">
    <br />
    <Container>
      <div class="form-inicio">
        <form @submit.prevent="GetCity()">
          <label for="local">Digite o nome da cidade para visualizar o tempo</label
          ><br /><br />
          <div class="form-button">
            <input
              type="text"
              v-model="local"
              placeholder="Cidade"
              id="local"
            />
            <button>Continuar</button>
          </div>
        </form>
      </div>
    </Container>

    <div class="dados" v-if="mostraDados">
      <div class="box1">
        <Container>
          <div class="img-formatada">
            <h1>
              <ion-icon name="location" style="color: tomato"></ion-icon> Local
            </h1>
            <img
              :src="`https://source.unsplash.com/600x400/?${dados.location.name},${dados.location.country}`"
              alt="Imagem mostrando a cidade"
            />
            <p>
              {{ dados.location.name }}, {{ dados.location.region }} -
              {{ dados.location.country }} <span style="color: grey">(Imagens não são 100% precisas)</span>
            </p>
          </div>
        </Container>
        <div>
          <Container>
            <h1><ion-icon name="calendar-outline"></ion-icon> Data</h1>
            <p>{{ dados.location.localtime }}</p>
          </Container>
          <Container>
            <div class="img-formatada">
              <div v-if="dados.current.is_day <= 0">
                <h1><ion-icon name="moon-outline"></ion-icon> Boa noite!</h1>
                <img
                  src="https://i.pinimg.com/originals/3f/92/3b/3f923b94ed539dd806d7a50168597bd0.gif"
                  alt="GIF representando noite"
                />
              </div>
              <div v-else>
                <h1>
                  <ion-icon name="sunny" style="color: orange"></ion-icon> Bom
                  dia!
                </h1>
                <img
                  src="https://64.media.tumblr.com/0107c41b38b5243a2edcbf763cc53117/tumblr_p6eny44Fxj1sdnqu4o1_500.gifv"
                  alt="GIF representando o dia"
                />
              </div>
            </div>
          </Container>
        </div>
      </div>

    <div class="box2">
      <Container>
        <h1>
          <ion-icon
            name="thermometer-outline"
            style="color: cornflowerblue"
          ></ion-icon>
          Temperatura
        </h1>
        <img :src="dados.current.condition.icon" alt="Condição do tempo" />
        <br />
        <progress :value="dados.current.temp_c" max="50">
          {{ dados.current.temp_c }}
        </progress>
        <span>{{ dados.current.temp_c }}ºC</span>
      </Container>
      <Container>
        <h1>
          <ion-icon name="flame" style="color: #ff471a"></ion-icon> Sensação
          térmica
        </h1>
        <p>{{ dados.current.feelslike_c }}ºC</p>
      </Container>
      <Container>
        <h1>
          <ion-icon name="thunderstorm-outline"></ion-icon> Condição climática
        </h1>
        <p>{{ dados.current.condition.text }}</p>
      </Container>
    </div>

    <div class="box1">
      <Container>
        <h1>
          <ion-icon name="water" style="color: #3399ff"></ion-icon>Umidade
        </h1>
        <p>{{ dados.current.humidity }}%</p>
      </Container>
      <Container>
        <h1>
          <ion-icon name="rocket" style="color: #6600ff"></ion-icon>Velocidade
          do vento
        </h1>
        <p>{{ dados.current.wind_kph }}km/h</p>
      </Container>
      </div>
      <br />
    </div>
  </div>
</template>

<script>
import Container from "./Container.vue";

export default {
  name: "Weather",
  components: {
    Container,
  },
  data() {
    return {
      local: null,
      dados: Array,
      mostraDados: false,
    };
  },
  methods: {
    async GetCity() {
      fetch(
        `https://api.weatherapi.com/v1/current.json?key=72a5449bd8aa4042934192245202211&q=${this.local}&aqi=no`
      )
        .then((response) => response.json())
        .then((data) => {
          this.dados = data;
          localStorage.setItem("Local", this.dados.location.name);
          this.mostraDados = true;
          this.$emit('change', this.dados.current.condition.text);
        });
    },
  },
  mounted() {
    this.local = localStorage.getItem("Local");
    this.GetCity();
  },
};
</script>

<style>
.form-button {
  display: grid;
  grid-template-columns: 70% 30%;
}

input {
  border: 2px solid grey;
  padding: 2%;
  border-radius: 10px;
  margin-right: 1%;
}

button {
  background: cornflowerblue;
  border: 0;
  padding: 2%;
  border-radius: 10px;
  color: white;
}

.img-formatada img {
  border-radius: 10px;
  width: 100%;
}

@media (min-width: 768px) {
  .box1 {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
  }

  .box2 {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
  }

  .container{
    text-align: center;
  }
}
</style>
