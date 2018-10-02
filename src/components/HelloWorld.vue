<template>
  <main id="main">
    <v-stepper v-model="e6" vertical>
    <v-stepper-step :complete="e6 > 1" step="1">Choose a label shape:</v-stepper-step>
    <v-stepper-content step="1">
      <v-card color="grey lighten-3" class="mb-5">
        <v-container fluid grid-list-sm>
          <v-layout>
            <v-flex xs6 sm3>
              <v-img src="https://cdn.vuetifyjs.com/images/parallax/material2.jpg"></v-img>
            </v-flex>

            <v-flex xs6 sm3>
              <v-img src="https://cdn.vuetifyjs.com/images/parallax/material2.jpg"></v-img>
            </v-flex>

            <v-flex xs6 sm3>
              <v-img src="https://cdn.vuetifyjs.com/images/parallax/material2.jpg"></v-img>
            </v-flex>

            <v-flex xs6 sm3>
              <v-img src="https://cdn.vuetifyjs.com/images/parallax/material2.jpg"></v-img>
            </v-flex>
          </v-layout>
          </v-container>
        </v-card>
        <v-toolbar class="white">
          <v-btn color="primary"><v-icon dark left>close</v-icon>Cancel</v-btn>
          <v-spacer></v-spacer>
          <v-btn color="primary" @click="e6 = 2">Next <v-icon dark right>arrow_forward</v-icon></v-btn>
        </v-toolbar>
      </v-stepper-content>

      <!-- Step 2 -->
      <v-stepper-step :complete="e6 > 2" step="2">Choose a label dimensions:</v-stepper-step>
      <v-stepper-content step="2">
        <v-card color="grey lighten-3" class="mb-5">
          <v-container fluid grid-list-sm>
            <v-layout>
              <v-flex xs12 sm12>
                <v-card-title class="headline font-weight-regular blue-grey white--text">Enter Your Label Dimensions</v-card-title>
                <v-form>
                  <v-container>
                    <v-layout wrap>
                      <v-flex xs12 md6>
                        <v-text-field label="Enter width" prepend-icon="swap_horiz"></v-text-field>
                      </v-flex>
                      <v-flex xs12 md6>
                        <v-text-field label="Enter height" prepend-icon="swap_vert"></v-text-field>
                      </v-flex>
                    </v-layout>
                  </v-container>
                </v-form>
              </v-flex>
            </v-layout>
          </v-container>
          <v-container fluid grid-list-sm>
            <v-layout>
              <v-flex xs12 sm12>
                <v-card-title class="headline font-weight-regular blue-grey white--text">Select Your Dimension</v-card-title>
                <v-form class="select-form">
                  <v-container>
                    <v-layout wrap>
                      <v-flex xs12 md12>
                        <a href="#"><v-subheader>1.5 X 3.0 (1-1/2 X 3) - Rounded Corners - Corner Radius 0.016</v-subheader></a>
                          <v-divider></v-divider>
                      </v-flex>
                      <v-flex xs12 md12>
                        <a href="#"><v-subheader>1.5 X 3.5 (1-1/2 X 3-1/2) - Rounded Corners - Corner Radius 0.063</v-subheader></a>
                          <v-divider></v-divider>
                      </v-flex>
                      <v-flex xs12 md12>
                        <a href="#"><v-subheader>1.75 X 3.5 (1-3/4 X 3-1/2) - Rounded Corners - Corner Radius 0.125</v-subheader></a>
                          <v-divider></v-divider>
                      </v-flex>
                      <v-flex xs12 md12>
                        <a href="#"><v-subheader>2.0 X 4.0 (2 X 4) - Rounded Corners - Corner Radius 0.125</v-subheader></a>
                          <v-divider></v-divider>
                      </v-flex>
                      <v-flex xs12 md12>
                        <a href="#"><v-subheader>2.0 X 5.0 (2 X 5) - Rounded Corners - Corner Radius 0.062</v-subheader></a>
                          <v-divider></v-divider>
                      </v-flex>
                    </v-layout>
                  </v-container>
                </v-form>
              </v-flex>
            </v-layout>
          </v-container>
        </v-card>
      <v-toolbar class="white">
        <v-btn color="primary" @click="e6 = 1"><v-icon dark left>arrow_back</v-icon>Back</v-btn>
        <v-btn color="primary"><v-icon dark left>close</v-icon>Cancel</v-btn>
        <v-spacer></v-spacer>
        <v-btn color="primary" @click="e6 = 3">Next <v-icon dark right>arrow_forward</v-icon></v-btn>
      </v-toolbar>
    </v-stepper-content>

    <v-stepper-step :complete="e6 > 3" step="3">Custom dues (CSV import)</v-stepper-step>
    <v-stepper-content step="3">
      <v-card color="grey lighten-2" class="mb-5" height="200px"></v-card>
      <v-toolbar class="white">
        <v-btn color="primary" @click="e6 = 2"><v-icon dark left>arrow_back</v-icon>Back</v-btn>
        <v-btn color="primary"><v-icon dark left>close</v-icon>Cancel</v-btn>
        <v-spacer></v-spacer>
        <v-btn color="primary" @click="e6 = 4">Next <v-icon dark right>arrow_forward</v-icon></v-btn>
      </v-toolbar>
    </v-stepper-content>

    <v-stepper-step :complete="e6 > 4" step="4">Choose Material</v-stepper-step>
    <v-stepper-content step="4">
      <v-card color="grey lighten-2" class="mb-5">
        <v-container fluid grid-list-sm>
          <v-card-title class="headline font-weight-regular blue-grey white--text">Most Popular</v-card-title>
          <v-layout row wrap>
            <v-flex v-for="i in 6" :key="`2${i}`" xs6 sm4 md2 >
              <v-card-text class="px-0"><v-img src="https://cdn.vuetifyjs.com/images/parallax/material2.jpg"></v-img></v-card-text>
            </v-flex>
          </v-layout>
          <v-card-title class="headline font-weight-regular blue-grey white--text">All Materials</v-card-title>
          <v-layout row wrap>
            <v-flex v-for="i in 18" :key="`2${i}`" xs6 sm4 md2 >
              <v-card-text class="px-0"><v-img src="https://cdn.vuetifyjs.com/images/parallax/material2.jpg"></v-img></v-card-text>
            </v-flex>
          </v-layout>
        </v-container>
      </v-card>
      <v-toolbar class="white">
        <v-btn color="primary" @click="e6 = 3"><v-icon dark left>arrow_back</v-icon>Back</v-btn>
        <v-btn color="primary"><v-icon dark left>close</v-icon>Cancel</v-btn>
        <v-spacer></v-spacer>
        <v-btn color="primary" @click="e6 = 5">Next <v-icon dark right>arrow_forward</v-icon></v-btn>
      </v-toolbar>
    </v-stepper-content>

    <v-stepper-step :complete="e6 > 5" step="5">Choose Laminate</v-stepper-step>
    <v-stepper-content step="5">
      <v-card color="grey lighten-2" class="mb-5">
        <v-container>
          <v-layout wrap id="laminate">
            <v-flex xs12 md12 white>
              <a href="#">
                <v-subheader color="white">HIGH GLOSS</v-subheader>
                <v-list-tile height="auto">Our most popular, and least expensive laminate. Provides protection and shiny finish.</v-list-tile>
              </a>
                <v-divider></v-divider>
            </v-flex>
            <v-flex xs12 md12 white>
              <a href="#">
                <v-subheader primary--text>MATTE</v-subheader>
                <v-list-tile height="auto">Our most popular, and least expensive laminate. Provides protection and shiny finish.</v-list-tile>
              </a>
                <v-divider></v-divider>
            </v-flex>
            <v-flex xs12 md12 white>
              <a href="#">
                <v-subheader>THERMAL TRANSFER</v-subheader>
                <v-list-tile height="auto">Our most popular, and least expensive laminate. Provides protection and shiny finish.</v-list-tile>
              </a>
                <v-divider></v-divider>
            </v-flex>
            <v-flex xs12 md12 white>
              <a href="#">
                <v-subheader>UV OUTDOOR GLOSS</v-subheader>
                <v-list-tile  height="auto">Our most popular, and least expensive laminate. Provides protection and shiny finish.</v-list-tile>
              </a>
                <v-divider></v-divider>
            </v-flex>
          </v-layout>
        </v-container>

      </v-card>
      <v-toolbar class="white">
        <v-btn color="primary" @click="e6 = 4"><v-icon dark left>arrow_back</v-icon>Back</v-btn>
        <v-btn color="primary"><v-icon dark left>close</v-icon>Cancel</v-btn>
        <v-spacer></v-spacer>
        <v-btn color="primary" @click="e6 = 6">Next <v-icon dark right>arrow_forward</v-icon></v-btn>
      </v-toolbar>
    </v-stepper-content>

    <v-stepper-step :complete="e6 > 6" step="6">Quantity of Order</v-stepper-step>
    <v-stepper-content step="6">
      <v-card color="grey lighten-2" class="mb-5">
        <v-container grid-list-md text-xs-center>
            <v-layout row wrap>
              <v-flex xs12>
                <v-form>
                  <v-container>
                    <!-- <v-divider></v-divider> -->
                    <v-card my-2 dark color="primary">
                      <v-layout row wrap>
                        <v-flex xs12 md6>
                          <v-card-title class="headline font-weight-regular">QUANTITY - How many labels do you need?</v-card-title>
                        </v-flex>
                        <v-flex xs12 md6>
                          <v-text-field :messages="['Minimum quantity 50 labels per version']" label="Enter Total Quantity"></v-text-field>
                        </v-flex>
                      </v-layout>
                      <v-divider></v-divider>
                    </v-card>
                     <v-divider></v-divider>
                     <v-card my-2 dark color="primary">
                      <v-layout row wrap>
                        <v-flex xs12 md6>
                          <v-card-title class="headline font-weight-regular">VERSONSI - How many different designs of this label do you need?</v-card-title>
                        </v-flex>
                        <v-flex xs12 md6>
                          <v-text-field :messages="['You must upload or email artwork for each version']" label="Enter # of Versions"></v-text-field>
                        </v-flex>
                      </v-layout>
                    </v-card>
                  </v-container>
                </v-form>
              </v-flex>
            </v-layout>
          </v-container>
      </v-card>
      <v-toolbar class="white">
        <v-btn color="primary" @click="e6 = 5"><v-icon dark left>arrow_back</v-icon>Back</v-btn>
        <v-btn color="primary"><v-icon dark left>close</v-icon>Cancel</v-btn>
        <v-spacer></v-spacer>
        <v-btn color="primary" @click="e6 = 7">Next <v-icon dark right>arrow_forward</v-icon></v-btn>
      </v-toolbar>
    </v-stepper-content>

    <v-stepper-step :complete="e6 > 7" step="7">Submission Form</v-stepper-step>
    <v-stepper-content step="7">
      <v-card color="grey lighten-2" class="mb-5" height="200px"></v-card>
      <v-toolbar class="white">
        <v-btn color="primary" @click="e6 = 6"><v-icon dark left>arrow_back</v-icon>Back</v-btn>
        <v-btn color="primary"><v-icon dark left>close</v-icon>Cancel</v-btn>
        <v-spacer></v-spacer>
        <v-btn color="primary">Get Quote Now <v-icon dark right>arrow_forward</v-icon></v-btn>
      </v-toolbar>
    </v-stepper-content>
  </v-stepper>
  </main>
  
</template>

<script>
export default {
  data () {
    return {
      e6: 1
    }
  },
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#main {
  margin: 2%;
}
v-card {
  height: auto;
}
.v-subheader {
  color: primary;
}
.v-list__tile {
  height: 200px !important;
}
.select-form {
  height: 270px;
  overflow-y: auto;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: primary;
  text-decoration: none;
}
</style>
