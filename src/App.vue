<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <div class="steps">
      <div class="step-item is-completed is-success">
        <div class="step-marker">
          <span class="icon">
            <i class="fa fa-check"></i>
          </span>
        </div>
        <div class="step-details">
          <p class="step-title">Shape</p>
          <p>This is the first step of the process.</p>
        </div>
      </div><!-- End 1 Step -->
      <div class="step-item is-active">
        <div class="step-marker"></div>
        <div class="step-details">
          <p class="step-title">Size</p>
          <p>This is the second step. You get here once you have completed the first step.</p>
        </div>
      </div><!-- End 2 Step -->
      <div class="step-item">
        <div class="step-marker">3</div>
        <div class="step-details">
          <p class="step-title">Material</p>
          <p>This is the third step. One more step before the end.</p>
      </div><!-- End 3 Step -->
      </div>
      <div class="step-item">
        <div class="step-marker">
          <span class="icon">
            <i class="fa fa-flag"></i>
          </span>
        </div>
        <div class="step-details">
          <p class="step-title">Laminate</p>
          <p>Final step. You have completed all the previous steps and end the process.</p>
        </div>
      </div><!-- End 4 step -->
      <div class="step-item">
        <div class="step-marker">
          <span class="icon">
            <i class="fa fa-flag"></i>
          </span>
        </div>
        <div class="step-details">
          <p class="step-title">Laminate</p>
          <p>Final step. You have completed all the previous steps and end the process.</p>
        </div>
      </div><!-- End 5 step -->
      <div class="step-item">
        <div class="step-marker">
          <span class="icon">
            <i class="fa fa-flag"></i>
          </span>
        </div>
        <div class="step-details">
          <p class="step-title">Quantity & Order Details</p>
          <p>Final step. You have completed all the previous steps and end the process.</p>
        </div>
      </div><!-- End 6 step -->
    </div>

  </div>
  
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    HelloWorld
  }
}
</script>

<style style lang="scss" rel="stylesheet/scss">
@import "../node_modules/bulma/bulma.sass";
@import "../node_modules/bulma-steps/dist/css/bulma-steps.sass";

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
