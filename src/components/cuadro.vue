<template>
<div class="my-2">

  <b-card no-body class="overflow-hidden" style="max-width: 540px;">
    <b-row no-gutters>
      <b-col md="6">
        <b-card-img :src="icon1Url" style="max-width:100px"></b-card-img>
        <h4>
            {{estado}}
          </h4>
      </b-col>
      <b-col md="6">
        <b-card-body :title="city">
          <b-card-text>
           {{temperatura}} C° 
          </b-card-text>
        </b-card-body>
      </b-col>
    </b-row>
  </b-card>


</div>

</template>

<script>
  // import axios from "axios";


export default {
   props:{ciudad:String},
  data(){
    return {
        icon1Url: require('@/assets/i_sol.png'),
        icon2Url: require('@/assets/i_nube.png'),
        icon3Url: require('@/assets/i_lluvia.png'),
        temperatura:0,
       
        city:'Paris',
        
        estado:'Clear',
        

      };
  },
  methods:{

      async mostrar()
      {
     
      const data  = await this.$http.get('http://api.openweathermap.org/data/2.5/weather?q='+ this.city +'&appid=7f8b2abd92901b3f89c16e2f87ac2409');
    
        const tem = data.data.main.temp;
        this.estado = data.data.weather[0].main;
        this.temperatura =Math.round( tem - 273.15);
        switch (this.estado) {
          case 'Clear':
            this.iconUrl= require('@/assets/i_sol.png');
            break;
          case 'Clouds':
            this.iconUrl= require('@/assets/i_nube.png');
            break;
          case 'Rain':
            this.iconUrl= require('@/assets/i_lluvia.png');
            break;
        }

      }
      },
  created(){
     this.mostrar();
  }
    
  }
</script>

