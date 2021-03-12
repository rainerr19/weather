<template>

<div class="container-fluid m-1" >
  <b-card overlay
    :img-src="imgUrl"
    img-height="400px"
  >
  
    <b-img v-bind:src="iconUrl" fluid class="md-6"></b-img>
    <b-card-text class="md-6">
    <h3 class="text-dark"><b>{{temperatura}} C° <br>{{ciudad}} <br>{{estado}}</b></h3>
    </b-card-text>

  </b-card>
 

</div>
</template>

<script>
// import axios from "axios";


export default {
   props:{ciudad:String},
  data(){
    return {
      imgUrl: require('@/assets/fondo.jpg'),
      iconUrl: require('@/assets/i_sol.png'),
      estado:'despejado',
      temperatura:25};
  },
 methods:{
  
    async mostrar()
      {
          const data  = await this.$http.get('http://api.openweathermap.org/data/2.5/weather?q=bogota&appid=7f8b2abd92901b3f89c16e2f87ac2409' );

        const tem = data.data.main.temp;
        this.estado = data.data.weather[0].main;
        this.temperatura =Math.round( tem - 273.15);
        switch (this.estado) {
          case 'Clear':
            this.imgUrl = require('@/assets/fondo.jpg');
            this.iconUrl= require('@/assets/i_sol.png');
            break;
          case 'Clouds':
            this.imgUrl = require('@/assets/nubes.jpg');
            this.iconUrl= require('@/assets/i_nube.png');
            break;
          case 'Rain':
            this.iconUrl= require('@/assets/i_lluvia.png');
            this.imgUrl = require('@/assets/lluvia.jpg');
            break;
        }
      }

    },
    created (){
      this.mostrar();
    }
    
  }
</script>

