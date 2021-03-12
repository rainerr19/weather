<template>

  <div class=" m-1">
    <div v-for="datos in valores" :key="datos.dt">


    <b-card >
      <div class="row">
        <div>
          <b-img left :src="datos.icon" style="max-width:70px"></b-img>
          <h5>
            {{datos.weather[0].main}}
          </h5>
        </div>
        <b-card-body :title="datos.day">
          <b-card-text>
            
            {{Math.round( datos.main.temp - 273.15)}} C° 
          </b-card-text>
        </b-card-body>
      </div>
    </b-card>
    </div>

 <!-- <b-card>
      <div class="row">
        <div>
          <b-img left :src="icon2Url" style="max-width:70px"></b-img>
          <h5>
            {{estado2}}
          </h5>
        </div>
        <b-card-body :title="dia2">
          <b-card-text>
            {{temperatura2}} C° 
          </b-card-text>
        </b-card-body>
      </div>
    </b-card> -->
     
  </div>


</template>

<script>
  // import axios from "axios";


export default {
  data(){
    return {
        dia1:'Friday',
        city:'Bogota',
        valores:{},
        days: ['Sunday','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday'],
        list:[]
      };
  },
 methods:{
  async mostrar(){
      //  const data  = await this.$http.get('http://api.openweathermap.org/data/2.5/forecast?q=bogota&cnt=18&appid=7f8b2abd92901b3f89c16e2f87ac2409' );
      const data = {"data":{"cod":"200","message":0,"cnt":18,"list":[{"dt":1615528800,"main":{"temp":284.92,"feels_like":285.02,"temp_min":284.67,"temp_max":284.92,"pressure":1021,"sea_level":1021,"grnd_level":751,"humidity":96,"temp_kf":0.25},"weather":[{"id":500,"main":"Rain","description":"light rain","icon":"10n"}],"clouds":{"all":74},"wind":{"speed":0.38,"deg":336},"visibility":10000,"pop":0.6,"rain":{"3h":0.23},"sys":{"pod":"n"},"dt_txt":"2021-03-12 06:00:00"},{"dt":1615539600,"main":{"temp":284.46,"feels_like":284.51,"temp_min":284.27,"temp_max":284.46,"pressure":1017,"sea_level":1017,"grnd_level":750,"humidity":96,"temp_kf":0.19},"weather":[{"id":500,"main":"Rain","description":"light rain","icon":"10n"}],"clouds":{"all":94},"wind":{"speed":0.27,"deg":358},"visibility":7103,"pop":0.66,"rain":{"3h":1.53},"sys":{"pod":"n"},"dt_txt":"2021-03-12 09:00:00"},{"dt":1615550400,"main":{"temp":284.45,"feels_like":284.29,"temp_min":284.4,"temp_max":284.45,"pressure":1017,"sea_level":1017,"grnd_level":752,"humidity":93,"temp_kf":0.05},"weather":[{"id":500,"main":"Rain","description":"light rain","icon":"10d"}],"clouds":{"all":96},"wind":{"speed":0.38,"deg":148},"visibility":10000,"pop":0.72,"rain":{"3h":2.74},"sys":{"pod":"d"},"dt_txt":"2021-03-12 12:00:00"},{"dt":1615561200,"main":{"temp":284.96,"feels_like":284.86,"temp_min":284.96,"temp_max":284.96,"pressure":1018,"sea_level":1018,"grnd_level":753,"humidity":92,"temp_kf":0},"weather":[{"id":500,"main":"Rain","description":"light rain","icon":"10d"}],"clouds":{"all":100},"wind":{"speed":0.43,"deg":207},"visibility":8171,"pop":0.81,"rain":{"3h":1.58},"sys":{"pod":"d"},"dt_txt":"2021-03-12 15:00:00"},{"dt":1615572000,"main":{"temp":285.45,"feels_like":285.42,"temp_min":285.45,"temp_max":285.45,"pressure":1014,"sea_level":1014,"grnd_level":751,"humidity":90,"temp_kf":0},"weather":[{"id":500,"main":"Rain","description":"light rain","icon":"10d"}],"clouds":{"all":100},"wind":{"speed":0.38,"deg":226},"visibility":10000,"pop":0.87,"rain":{"3h":1.37},"sys":{"pod":"d"},"dt_txt":"2021-03-12 18:00:00"},{"dt":1615582800,"main":{"temp":286.78,"feels_like":286.73,"temp_min":286.78,"temp_max":286.78,"pressure":1011,"sea_level":1011,"grnd_level":749,"humidity":82,"temp_kf":0},"weather":[{"id":500,"main":"Rain","description":"light rain","icon":"10d"}],"clouds":{"all":98},"wind":{"speed":0.38,"deg":261},"visibility":10000,"pop":0.91,"rain":{"3h":0.54},"sys":{"pod":"d"},"dt_txt":"2021-03-12 21:00:00"},{"dt":1615593600,"main":{"temp":284.45,"feels_like":284.43,"temp_min":284.45,"temp_max":284.45,"pressure":1014,"sea_level":1014,"grnd_level":750,"humidity":93,"temp_kf":0},"weather":[{"id":500,"main":"Rain","description":"light rain","icon":"10n"}],"clouds":{"all":92},"wind":{"speed":0.17,"deg":127},"visibility":10000,"pop":0.87,"rain":{"3h":0.82},"sys":{"pod":"n"},"dt_txt":"2021-03-13 00:00:00"},{"dt":1615604400,"main":{"temp":284.11,"feels_like":283.9,"temp_min":284.11,"temp_max":284.11,"pressure":1016,"sea_level":1016,"grnd_level":751,"humidity":93,"temp_kf":0},"weather":[{"id":500,"main":"Rain","description":"light rain","icon":"10n"}],"clouds":{"all":87},"wind":{"speed":0.32,"deg":123},"visibility":10000,"pop":0.81,"rain":{"3h":0.29},"sys":{"pod":"n"},"dt_txt":"2021-03-13 03:00:00"},{"dt":1615615200,"main":{"temp":283.97,"feels_like":283.9,"temp_min":283.97,"temp_max":283.97,"pressure":1015,"sea_level":1015,"grnd_level":750,"humidity":93,"temp_kf":0},"weather":[{"id":500,"main":"Rain","description":"light rain","icon":"10n"}],"clouds":{"all":84},"wind":{"speed":0.06,"deg":268},"visibility":10000,"pop":0.85,"rain":{"3h":0.15},"sys":{"pod":"n"},"dt_txt":"2021-03-13 06:00:00"},{"dt":1615626000,"main":{"temp":283.69,"feels_like":283.41,"temp_min":283.69,"temp_max":283.69,"pressure":1014,"sea_level":1014,"grnd_level":749,"humidity":94,"temp_kf":0},"weather":[{"id":500,"main":"Rain","description":"light rain","icon":"10n"}],"clouds":{"all":100},"wind":{"speed":0.32,"deg":351},"visibility":10000,"pop":0.75,"rain":{"3h":0.66},"sys":{"pod":"n"},"dt_txt":"2021-03-13 09:00:00"},{"dt":1615636800,"main":{"temp":284.22,"feels_like":284.11,"temp_min":284.22,"temp_max":284.22,"pressure":1017,"sea_level":1017,"grnd_level":751,"humidity":93,"temp_kf":0},"weather":[{"id":500,"main":"Rain","description":"light rain","icon":"10d"}],"clouds":{"all":100},"wind":{"speed":0.22,"deg":290},"visibility":10000,"pop":0.79,"rain":{"3h":1.59},"sys":{"pod":"d"},"dt_txt":"2021-03-13 12:00:00"},{"dt":1615647600,"main":{"temp":286.16,"feels_like":286.15,"temp_min":286.16,"temp_max":286.16,"pressure":1018,"sea_level":1018,"grnd_level":754,"humidity":87,"temp_kf":0},"weather":[{"id":500,"main":"Rain","description":"light rain","icon":"10d"}],"clouds":{"all":100},"wind":{"speed":0.44,"deg":242},"visibility":10000,"pop":0.9,"rain":{"3h":2.57},"sys":{"pod":"d"},"dt_txt":"2021-03-13 15:00:00"},{"dt":1615658400,"main":{"temp":288.6,"feels_like":288.3,"temp_min":288.6,"temp_max":288.6,"pressure":1014,"sea_level":1014,"grnd_level":753,"humidity":77,"temp_kf":0},"weather":[{"id":500,"main":"Rain","description":"light rain","icon":"10d"}],"clouds":{"all":99},"wind":{"speed":1.07,"deg":270},"visibility":10000,"pop":0.95,"rain":{"3h":1.7},"sys":{"pod":"d"},"dt_txt":"2021-03-13 18:00:00"},{"dt":1615669200,"main":{"temp":287.89,"feels_like":287.77,"temp_min":287.89,"temp_max":287.89,"pressure":1011,"sea_level":1011,"grnd_level":750,"humidity":83,"temp_kf":0},"weather":[{"id":500,"main":"Rain","description":"light rain","icon":"10d"}],"clouds":{"all":82},"wind":{"speed":1.01,"deg":273},"visibility":7539,"pop":0.89,"rain":{"3h":2.18},"sys":{"pod":"d"},"dt_txt":"2021-03-13 21:00:00"},{"dt":1615680000,"main":{"temp":284.69,"feels_like":284.65,"temp_min":284.69,"temp_max":284.69,"pressure":1013,"sea_level":1013,"grnd_level":749,"humidity":93,"temp_kf":0},"weather":[{"id":500,"main":"Rain","description":"light rain","icon":"10n"}],"clouds":{"all":86},"wind":{"speed":0.3,"deg":89},"visibility":9061,"pop":0.95,"rain":{"3h":1.66},"sys":{"pod":"n"},"dt_txt":"2021-03-14 00:00:00"},{"dt":1615690800,"main":{"temp":284.07,"feels_like":283.68,"temp_min":284.07,"temp_max":284.07,"pressure":1016,"sea_level":1016,"grnd_level":751,"humidity":92,"temp_kf":0},"weather":[{"id":500,"main":"Rain","description":"light rain","icon":"10n"}],"clouds":{"all":97},"wind":{"speed":0.5,"deg":90},"visibility":10000,"pop":0.97,"rain":{"3h":0.55},"sys":{"pod":"n"},"dt_txt":"2021-03-14 03:00:00"},{"dt":1615701600,"main":{"temp":284.19,"feels_like":283.86,"temp_min":284.19,"temp_max":284.19,"pressure":1015,"sea_level":1015,"grnd_level":750,"humidity":92,"temp_kf":0},"weather":[{"id":500,"main":"Rain","description":"light rain","icon":"10n"}],"clouds":{"all":98},"wind":{"speed":0.46,"deg":9},"visibility":10000,"pop":0.91,"rain":{"3h":0.39},"sys":{"pod":"n"},"dt_txt":"2021-03-14 06:00:00"},{"dt":1615712400,"main":{"temp":283.84,"feels_like":283.41,"temp_min":283.84,"temp_max":283.84,"pressure":1015,"sea_level":1015,"grnd_level":750,"humidity":93,"temp_kf":0},"weather":[{"id":500,"main":"Rain","description":"light rain","icon":"10n"}],"clouds":{"all":100},"wind":{"speed":0.53,"deg":304},"visibility":10000,"pop":0.6,"rain":{"3h":0.26},"sys":{"pod":"n"},"dt_txt":"2021-03-14 09:00:00"}],"city":{"id":3688689,"name":"Bogotá","coord":{"lat":4.6097,"lon":-74.0817},"country":"CO","population":1000000,"timezone":-18000,"sunrise":1615460650,"sunset":1615504113}}};
      this.list = data.data.list;
      
      for (let i = 0; i < this.list.length; i+=8) {
        this.valores[i] = this.list[i];
        
        var d = new Date(this.list[i].dt_txt);
        this.valores[i].day = this.days[ d.getDay() ]
        switch (this.valores[i].weather[0].main) {
          case 'Clear':
            this.valores[i].icon = require('@/assets/i_sol.png');
            break;
          case 'Clouds':
            this.valores[i].icon = require('@/assets/i_nube.png');
            break;
          case 'Rain':
            this.valores[i].icon = require('@/assets/i_lluvia.png');
            break;
        }
      }
    }
 },created(){
  

        this.mostrar();
    }
}
</script>

