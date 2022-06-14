<template>
  <div class="home">
    <div class="mt-10 mx-10">
      <v-text-field
        solo
        label="Search Service"
        prepend-inner-icon="mdi-magnify"
        v-model="search"
      ></v-text-field>

      <v-form>
        <v-row class="justify-end">
          <v-icon color="blue" class="mr-6">mdi-plus-circle-outline</v-icon>

         

  
    <v-dialog
      v-model="dialog"
      persistent
      max-width="600px"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="blue" text
          dark
          v-bind="attrs"
          v-on="on"
         
        >
          ADD SERVICE
        </v-btn>
      </template>
      <v-card>
        <v-card-title>
          <span class="text-h5">Add Sevices</span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >      
                <v-text-field
                  label="Title"
                  v-model="newServiceTitle"
                ></v-text-field>
              </v-col>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >
                <v-text-field
                  label="Description"
                  v-model="newDescription"
                ></v-text-field>
              </v-col>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >
                <v-text-field
                  label="Price"
                v-model="newPrice"
                ></v-text-field>
              </v-col>
    
              <v-col
                cols="12"
                sm="6"
              >
         
              </v-col>
            </v-row>
          </v-container>
        
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="blue darken-1"
            text
            @click="dialog = false"
          >
            Close
          </v-btn>
          <v-btn
            color="blue darken-1"
            text
            @click="addService"

            
             
          >
            Save
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>

        </v-row>
      </v-form>
    </div>
    <v-card class="mx-auto mt-4" outlined>
      <div v-for="service in filteredSearch" :key="service.id">
        <v-list-item three-line>
          <v-list-item-avatar tile size="80" color="grey"></v-list-item-avatar>
          <v-list-item-content>
            <div class="text-overline text-h1">
              {{ service.title }}
            </div>
            <v-list-item-title class="text-overline text-h6">
              {{ service.description }}
            </v-list-item-title>
            <v-list-item-subtitle
              ><v-icon>mdi-currency-php</v-icon> {{ service.price }}.00/ Session</v-list-item-subtitle
            >
          </v-list-item-content>
        </v-list-item>
        <v-divider></v-divider>
      </div>
    </v-card>
  
    <div class="mt-10 mx-3">
      <v-card class="rounded-xl mb-7" color="#1E88E5" >
        <v-row>
          <v-card-title class="text-h6 ml-4 white--text" dark>
            Cart . 5 items
          </v-card-title>
          <v-card-title class="text-h6 ml-10 white--text">
             <v-icon>mdi-currency-php</v-icon>350.00
          </v-card-title>
        </v-row>
      </v-card>
    </div>
  </div>
</template>

<script>
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Home",
  data() {
    return {
      services: [
        {
          id: 1,
          title: "Walk-in Gym Use",
          description: "Access to gym facilities for a day 5",
          price: "100",
        },
        {
          id: 2,
          title: "Reular Monthly Membership",
          description: "Regular access to gym facilities per month",
          price: "1,250",
        },
        {
          id: 3,
          title: "Boxing Session",
          description: "Boxing with coach per session",
          price: "500",
        },
      ],
      search:'',
      dialog: false,
      newServiceTitle: '',
      newPrice: '',
      newDescription: '',
    };
  },
  components: {
    HelloWorld,
  },
  methods: {
    addService() {
     let newService = {
      id: Date.now(),
      title: this.newServiceTitle,
      description: this.newDescription,
      price: this.newPrice,
     }
     this.services.push(newService)
     this.newServiceTitle = ''
     this.newDescription = ''
     this.newPrice = ''
    }
  },
  computed: {
    filteredSearch: function () {
     return this.services.filter((service) => {
        return service.title.match(this.search)
      })
    }
  }
};
</script>
