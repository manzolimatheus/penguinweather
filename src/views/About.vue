<template>
  <div class="about">
    <div class="content">
      <br>
      <h1>Feito por Matheus Manzoli 🐧</h1>
      <iframe src="https://embed.lottiefiles.com/animation/2448"></iframe>
      <h1>Tecnologias</h1>
      <br>
      <div class="logos">
        <img src="https://cdn.weatherapi.com/v4/images/weatherapi_logo.png" alt="Logo da WeatherAPI" title="WeatherAPI">
        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/95/Vue.js_Logo_2.svg/1184px-Vue.js_Logo_2.svg.png" alt="Logo Vue.js" title="Vue.js">
        <img src="https://img.stackshare.io/service/5368/icon.png" alt="Logo do Ionicons" style="clip-path: circle();" title="Ionicons">
        <img src="https://avatars.githubusercontent.com/u/30947444?v=4" alt="Logo Lottie files" title="LottieFiles">
        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/ed/Logo_of_Unsplash.svg/1024px-Logo_of_Unsplash.svg.png" alt="Logo Unsplash">
      </div>
      <br>
    </div>
  </div>
</template>

<script>
export default {
  name: "About",
};
</script>

<style>
body {
  background-color: cornflowerblue;
}

.content {
  display: grid;
  justify-content: center;
  align-items: center;
  text-align: center;
  color: white;
  padding: 5%;
  height: 100vh;
}

iframe{
  border: 0;
  width: 100%;
  height: 300px;
}

.logos img{
  width: 50px;
  height: auto;
  padding-inline: 2%;
}
</style>
