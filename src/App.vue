<template>
  <Nav />
  <router-view />
  <Footer />
</template>

<script>
import Nav from "@/components/Nav.vue";
import Footer from "@/components/Footer.vue";

export default {
  components: {
    Nav,
    Footer
  },
};
</script>


<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@700&family=Roboto+Condensed&display=swap");

* {
  padding: 0;
  margin: 0;
  font-family: "Roboto Condensed", sans-serif;
}

a,
h3 {
  color: white;
  text-decoration: none;
  padding-inline: 1%;
  font-family: "Montserrat", sans-serif;
}

/* Scrollbar */
/* width */
::-webkit-scrollbar {
  width: 10px;
}
/* Track */
::-webkit-scrollbar-track {
  background: #f1f1f1;
}
/* Handle */
::-webkit-scrollbar-thumb {
  background: rgb(187, 187, 187);
  border-radius: 10px;
}
/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #555;
}
</style>
