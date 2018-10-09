<template>
  <main id="main">
    <v-stepper v-model="e6" vertical>
    <v-stepper-step class="white--text" :complete="e6 > 1" step="1">Choose a label shape:</v-stepper-step>
    <v-stepper-content step="1">
      <v-card dark color="lighten-3 grey" class="mb-5">
        <v-container fluid grid-list-sm>
          <v-layout>
            <v-flex xs6 sm3 v-for="(imgLabelShape, index) in labelsShapes" :key="`imgLabelShape-${index = index + 2}`" >
              <v-img  :src="imgLabelShape.url" ></v-img>
              <button flat class="mt-4 ml-0 select-btn " :class="{ 'active':imgLabelShape == request.selectedShape }" @click="getImgTitle, request.selectedShape = imgLabelShape" :data-title="imgLabelShape.title">{{imgLabelShape.title}}</button>
            </v-flex>
          </v-layout>
          </v-container>
          <v-toolbar class="grey lighten-3">
          <v-btn color="primary"><v-icon dark left>close</v-icon>Cancel</v-btn>
          <v-spacer></v-spacer>
          <v-btn color="primary" @click="e6 = 2">Next <v-icon dark right>arrow_forward</v-icon></v-btn>
        </v-toolbar>
        </v-card>
        
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
                        <v-text-field v-model="request.labelDimensions.width" name="width" label="Enter width" prepend-icon="swap_horiz"></v-text-field>
                      </v-flex>
                      <v-flex xs12 md6>
                        <v-text-field v-model="request.labelDimensions.height" name="height" label="Enter height" prepend-icon="swap_vert"></v-text-field>
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
                      <v-flex xs12 md12 v-for="(dimension, i) in dimensions" :key="`dimension-${i}`">
                        <v-subheader>
                          <v-checkbox v-model="request.labelDimensions.dimension" :value="dimension" :label="dimension" required></v-checkbox>
                        </v-subheader>
                        <v-divider></v-divider>
                      </v-flex>
                    </v-layout>
                  </v-container>
                </v-form>
              </v-flex>
            </v-layout>
          </v-container>
          <v-toolbar class="grey lighten-3">
        <v-btn color="primary" @click="e6 = 1"><v-icon dark left>arrow_back</v-icon>Back</v-btn>
        <v-btn color="primary"><v-icon dark left>close</v-icon>Cancel</v-btn>
        <v-spacer></v-spacer>
        <v-btn color="primary" @click="e6 = 3">Next <v-icon dark right>arrow_forward</v-icon></v-btn>
      </v-toolbar>
        </v-card>
    </v-stepper-content>


    <v-stepper-step :complete="e6 > 3" step="3">Custom dues (CSV import)</v-stepper-step>
    <v-stepper-content step="3">
      <v-card color="grey lighten-3" class="mb-5">
        <h1>STEP 3</h1>
        <v-toolbar color="grey lighten-3">
        <v-btn color="primary" @click="e6 = 2"><v-icon dark left>arrow_back</v-icon>Back</v-btn>
        <v-btn color="primary"><v-icon dark left>close</v-icon>Cancel</v-btn>
        <v-spacer></v-spacer>
        <v-btn color="primary" @click="e6 = 4">Next <v-icon dark right>arrow_forward</v-icon></v-btn>
      </v-toolbar>
      </v-card>
      
    </v-stepper-content>

    <!-- Step 4 -->
    <v-stepper-step :complete="e6 > 4" step="4">Choose Material</v-stepper-step>
    <v-stepper-content step="4">
      <v-card color="grey lighten-3" class="mb-5">
        <v-container fluid grid-list-sm>
          <v-card-title class="headline font-weight-regular blue-grey white--text">All Materials</v-card-title>
          <v-layout row wrap>
            <v-flex v-for="(material, i) in materials" :key="`material-${i++} + 3`" xs6 sm4 md2 >
              <v-card-text class="px-0">
                <v-img :src="material.url"></v-img>
                <button flat class="mt-4 ml-0 select-btn" :class="{ 'active':material == request.selectedMaterial }" @click="getImgTitle, request.selectedMaterial = material" :data-title="material.title">{{ material.title }}</button>
              </v-card-text>
            </v-flex>
          </v-layout>
        </v-container>
        <v-toolbar class="grey lighten-3">
        <v-btn color="primary" @click="e6 = 3"><v-icon dark left>arrow_back</v-icon>Back</v-btn>
        <v-btn color="primary"><v-icon dark left>close</v-icon>Cancel</v-btn>
        <v-spacer></v-spacer>
        <v-btn color="primary" @click="e6 = 5">Next <v-icon dark right>arrow_forward</v-icon></v-btn>
      </v-toolbar>
      </v-card>
    </v-stepper-content>

    <!-- Step 5 -->
    <v-stepper-step :complete="e6 > 5" step="5">Choose Laminate</v-stepper-step>
    <v-stepper-content step="5">
      <v-card color="grey lighten-3" class="mb-5">
        <v-container>
          <v-layout wrap id="laminate">
            <v-flex xs12 md12 v-for="(laminate, i) in laminates" :key="`laminate-${i}`">
              <a href="#">
                <v-subheader color="grey lighten-3"> 
                  <v-checkbox v-model="request.laminate" :value="laminate.title" :label="laminate.title" required></v-checkbox>
                </v-subheader>
                <v-list-tile height="auto">{{ laminate.description }}</v-list-tile>
              </a>
              <v-divider></v-divider>
            </v-flex>
          </v-layout>
        </v-container>
        <v-toolbar class="grey lighten-3">
        <v-btn color="primary" @click="e6 = 4"><v-icon dark left>arrow_back</v-icon>Back</v-btn>
        <v-btn color="primary"><v-icon dark left>close</v-icon>Cancel</v-btn>
        <v-spacer></v-spacer>
        <v-btn color="primary" @click="e6 = 6">Next <v-icon dark right>arrow_forward</v-icon></v-btn>
      </v-toolbar>
      </v-card>
      
    </v-stepper-content>

    <v-stepper-step :complete="e6 > 6" step="6">Quantity of Order</v-stepper-step>
    <v-stepper-content step="6">
      <v-card color="grey lighten-3" class="mb-5">
        <v-container fluid grid-list-sm>
            <v-layout>
              <v-flex xs12 sm12>
                <v-card-title class="headline font-weight-regular blue-grey white--text">How many labels & different designs of this label do you need?</v-card-title>
                <v-form>
                  <v-container>
                    <v-layout wrap>
                      <v-flex px-5 xs12 md6>
                        <v-text-field v-model="request.quantitysOfOrder.quantity" :messages="['Minimum quantity 50 labels per version']" label="Enter Total Quantity"></v-text-field>
                      </v-flex>
                      <v-flex px-5 xs12 md6>
                        <v-text-field v-model="request.quantitysOfOrder.versions" :messages="['You must upload or email artwork for each version']" label="Enter # of Versions"></v-text-field>
                      </v-flex>
                    </v-layout>
                  </v-container>
                </v-form>
              </v-flex>
            </v-layout>
          </v-container>
          <v-toolbar class="grey lighten-3">
        <v-btn color="primary" @click="e6 = 5"><v-icon dark left>arrow_back</v-icon>Back</v-btn>
        <v-btn color="primary"><v-icon dark left>close</v-icon>Cancel</v-btn>
        <v-spacer></v-spacer>
        <v-btn color="primary" @click="e6 = 7">Next <v-icon dark right>arrow_forward</v-icon></v-btn>
      </v-toolbar>
      </v-card>
      
    </v-stepper-content>

    <v-stepper-step class="white--text" :complete="e6 > 7" step="7">Submission Form</v-stepper-step>
    <v-stepper-content step="7">
      <v-card color="grey lighten-3" class="mb-5">
        <v-container fluid grid-list-sm>
            <v-layout row wrap>
              <v-flex xs12 md12>
                 <v-card-title class="headline font-weight-regular blue-grey white--text">Get Quote Now!</v-card-title>
                <v-form>
                  <v-container>
                    <!-- <v-divider></v-divider> -->
                    <v-card class="card-quantity my-2 dark" color="white">
                      <v-layout row wrap>
                        <v-flex xs12 md10>
                          <v-text-field v-model="request.submisionForm.name" label="Enter Your Name" prepend-icon="perm_identity"></v-text-field>
                        </v-flex>
                      </v-layout>
                    </v-card>
                     <v-card class="card-quantity my-2 dark" color="white">
                      <v-layout row wrap>
                        <v-flex xs12 md10>
                          <v-text-field v-model="request.submisionForm.job" label="Enter Your Bussines Name" prepend-icon="work"></v-text-field>
                        </v-flex>
                      </v-layout>
                    </v-card>
                    <v-card class="card-quantity my-2 dark" color="white">
                      <v-layout row wrap>
                        <v-flex xs12 md10>
                          <v-text-field v-model="request.submisionForm.phone" label="Enter Your Phone" prepend-icon="phone"></v-text-field>
                        </v-flex>
                      </v-layout>
                    </v-card>
                    <v-card class="card-quantity my-2 dark" color="white">
                      <v-layout row wrap>
                        <v-flex xs12 md10>
                          <v-text-field v-model="request.submisionForm.email" label="Enter Your Email" prepend-icon="email"></v-text-field>
                        </v-flex>
                      </v-layout>
                    </v-card>
                  </v-container>
                </v-form>
              </v-flex>
            </v-layout>
          </v-container>
          <v-toolbar class="grey lighten-3">
        <v-btn color="primary" @click="e6 = 6"><v-icon dark left>arrow_back</v-icon>Back</v-btn>
        <v-btn color="primary"><v-icon dark left>close</v-icon>Cancel</v-btn>
        <v-spacer></v-spacer>
        <v-btn color="primary">Get Quote Now <v-icon dark right>arrow_forward</v-icon></v-btn>
      </v-toolbar>
      </v-card>
      
    </v-stepper-content>
  </v-stepper>
  </main>
  
</template>

<script>
export default {
  name: 'Request',
  props: {
    msg: String
  },
  data () {
    return {
      e6: 1,
      request: {
        selectedShape: false,
        selectedMaterial: false,
        labelDimensions: {
          width: null,
          height: null,
          dimension: []
        },
        material: {
          title: "",
          url: ""
        },
        laminate: [],
        quantitysOfOrder: {
          quantity: null,
          versions: null,
        },
        submisionForm: {
          name: null,
          job: null,
          phone: null,
          email: null
        }
      },

      labelsShapes: [
          {url: "https://cdn.vuetifyjs.com/images/parallax/material2.jpg", title: "Rectangle"}, 
          {url: "https://cdn.vuetifyjs.com/images/parallax/material2.jpg", title: "Square"}, 
          {url: "https://cdn.vuetifyjs.com/images/parallax/material2.jpg", title: "Oval"}, 
          {url: "https://cdn.vuetifyjs.com/images/parallax/material2.jpg", title: "Circle"},
        ],
      dimensions: [
        "1.5 X 3.0 (1-1/2 X 3) - Rounded Corners - Corner Radius 0.016",
        "1.5 X 3.5 (1-1/2 X 3-1/2) - Rounded Corners - Corner Radius 0.063",
        "1.75 X 3.5 (1-3/4 X 3-1/2) - Rounded Corners - Corner Radius 0.125",
        "2.0 X 4.0 (2 X 4) - Rounded Corners - Corner Radius 0.125",
        "2.0 X 5.0 (2 X 5) - Rounded Corners - Corner Radius 0.062",
        "1.5 X 3.0 (1-1/2 X 3) - Rounded Corners - Corner Radius 0.0145",
        "1.5 X 3.5 (1-1/2 X 3-1/2) - Rounded Corners - Corner Radius 0.06345",
        "1.75 X 3.5 (1-3/4 X 3-1/2) - Rounded Corners - Corner Radius 0.12575",
        "2.0 X 4.0 (2 X 4) - Rounded Corners - Corner Radius 0.12515",
        "2.0 X 5.0 (2 X 5) - Rounded Corners - Corner Radius 0.062753",
      ],
      materials: [
          {url: "https://cdn.vuetifyjs.com/images/parallax/material2.jpg", title: "CAST GLOSS"}, 
          {url: "https://cdn.vuetifyjs.com/images/parallax/material2.jpg", title: "CHROME BOPP"}, 
          {url: "https://cdn.vuetifyjs.com/images/parallax/material2.jpg", title: "CHROME BOPP (LIP BALM)"}, 
          {url: "https://cdn.vuetifyjs.com/images/parallax/material2.jpg", title: "GOLD BOPP"},
          {url: "https://cdn.vuetifyjs.com/images/parallax/material2.jpg", title: "WHITE BOPP"},
          {url: "https://cdn.vuetifyjs.com/images/parallax/material2.jpg", title: "VELLUM- RECYCLED"}, 
          {url: "https://cdn.vuetifyjs.com/images/parallax/material2.jpg", title: "SQUEEZABLE"}, 
          {url: "https://cdn.vuetifyjs.com/images/parallax/material2.jpg", title: "WHITE VINYL"},
      ],
      laminates: [
        {title: "HIGH GLOSS", description: "Our most popular, and least expensive laminate. Provides protection and shiny finish."},
        {title: "MATTE", description: "Provides a dull, non-glossy finish. Achieves a more 'natural' look."},
        {title: "THERMAL TRANSFER", description: "Gloss laminate that works with most thermal transfer printers."},
        {title: "UV OUTDOOR GLOSS", description: "Best for labels that will be used outdoors. High gloss finish, with UV resistance."},
      ]
    }
  },
  methods: {
    getImgTitle: function(e) {
      this.imgLabelShape.title = e.target.dataset.title;
    },
  },
  computed: {
    compClasses() {
      return {
        selectedShape: this.selectedShape,
        selectedMaterial: this.selectedMaterial,
      }
    }
  }
}
</script>

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
.card-quantity {
  margin: 20px 0;
  padding: 20px;
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

.theme--light.v-stepper,
.theme--light.v-toolbar {
  background-color: transparent;
}
.select-btn {
  width: 100%;
  padding: 10px;
  text-transform: uppercase;
  background: #9e9e9e;
  color: #fff;
}
.v-stepper--vertical .v-stepper__step {
  color: #fff !important;
  text-transform: uppercase;
}
.theme--light.v-stepper .v-stepper__step--active .v-stepper__label {
  color: #fff !important;
  text-transform: uppercase;
}
button.active {
  background: #1976d2;
}
</style>
