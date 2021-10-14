<template>
  <div id="nav">
    <header>
      <br />
      <router-link to="/">🐧Penguinweather</router-link>
    </header>
    <br />
    <!-- Nav PC -->
    <nav class="pc">
      <div></div>
      <div>
        <router-link to="/">Início</router-link>
        <router-link to="/about">Sobre</router-link>
      </div>
      <div></div>
    </nav>
  </div>
</template>

<script>
export default {
  name: "Nav",
};
</script>

<style>
#nav {
  background: black;
  text-align: center;
  padding: 1%;
}

.pc {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
}

.pc a {
  padding-inline: 10%;
}
</style>