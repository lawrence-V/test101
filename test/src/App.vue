<template>
  <v-app id="inspire">
    <v-navigation-drawer 
    v-model="drawer"
    absolute
      temporary
    >
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h6">
            Point of sale
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>
      <v-divider></v-divider>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.to"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>


    <v-app-bar
      absolute
      color="#1E88E5"
      dark
      prominents
    
    >
  

          <v-app-bar-nav-icon @click="drawer = true">
            <v-icon>mdi-chevron-left</v-icon>
      </v-app-bar-nav-icon>

      <v-toolbar-title>Point of sale</v-toolbar-title>

      <v-spacer></v-spacer>





      <template v-slot:extension>
        <v-tabs align-with-title>
          <v-tab to="/">Sevices</v-tab>
          <v-tab to="/products">Products</v-tab>

        </v-tabs>
      </template>
    </v-app-bar>
  <div class="mt-6">
    
  </div>

       <div class="mt-10">
       <v-main class="mt-10">
     <router-view></router-view>
    </v-main>
    </div>

 
     

        
  </v-app>
</template>

<script>
  export default {
    data: () => ({
       items: [
          { title: 'Service', icon: 'mdi-view-dashboard' ,to : '/'},
          { title: 'Products', icon: 'mdi-help-box', to : '/products'},
        ],
       drawer: false
        }),
  }
</script>