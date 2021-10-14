<template>
  <div class="home" :style="{backgroundImage: `linear-gradient(#00000080, rgba(0, 0, 0, 0.7)),url('${url}')`, backgroundRepeat: 'no-repeat', backgroundAttachment: 'fixed', backgroundSize: 'cover', backgroundPosition: 'center'}">
    <Weather @change="ChangeBackground" />
  </div>
</template>

<script>

import Weather from '@/components/Weather.vue'

export default {
  name: 'Home',
  components:{
    Weather
  },
  data(){
    return{
      url: null
    }
  },
  methods:{
    ChangeBackground(e){
      this.url = `https://source.unsplash.com/featured/?${e}`
    }
  }
}
</script>

<style>
.home{
  width: 100%;
  height: 100%;
}


</style>
