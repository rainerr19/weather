<template>
  <div id="app">
      <div class="container-fluid mt-2">
        <div class="row justify-content-center">
          <div class="col-md-10">
              <panel ciudad="Bogota" />
            <div class="row">
              <div class="col-md-6">
              <cuadro3tiempos/>
              </div>
              <div class="col-md-6">
              <cuadro  ciudad="Londres" />
              </div>

            </div>
            
          </div>
                
              
        </div>
      </div>
  </div>
</template>

<script>
import panel from './components/cuadroTiempo.vue'
import cuadro from './components/cuadro.vue'
import cuadro3tiempos from './components/cuadro3tiempos.vue'

export default {
  name: 'App',
  components: {
    panel,cuadro3tiempos,cuadro
  }
}
</script>

