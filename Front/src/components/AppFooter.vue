<template>
  <v-footer
    app
    absolute
    color="error"
    padless
  >
    <v-row
      absolute
      justify="center"
      no-gutters>
      <v-col
        cols="12"
        md="3"
        height="100%"
        class="py-4 text-center white--text" 
        align-self="center"
        >
          {{ new Date().getFullYear() }} — <strong>{{appName}}</strong>
      </v-col>
      <v-col
        cols="12"
        md="9"
        align="center"
        class=".d-none"
        v-if="$vuetify.breakpoint.mdAndUp">
        <v-card color="transparent">
          <v-card-title class="text-center white--text" >Categorias</v-card-title>
          <v-divider color="white"/>
          <v-chip v-for="cat in eventCategories" :key="cat"
          class="ma-2"
          outlined
          pill
          color="white">
          {{cat}}
        </v-chip>
        </v-card>
        
      </v-col>
      <v-col
        cols="12"
        align="right"
        align-self="center"
        v-if="$vuetify.breakpoint.smAndDown">
          <div v-for="(link, index) in navLinks" 
              :key="link.name">
            <v-btn
              v-if="link.show"
              :to="{name:`${link.name}`}"
              @click="changeLoginMenuButtons(index)"
              plain
              dark
              class="my-2 d-flex d-md-inline-flex"
            >
              
              <v-icon class="pb-1 pr-1">{{link.icon}}</v-icon>
              {{ link.text }}
            </v-btn>
            
          </div>
      </v-col>
    </v-row>
  </v-footer>
</template>

<script>

import {mapState, mapActions} from 'vuex'

export default ({
  computed:{
    ...mapState('globals', ['appName','navLinks']),
    ...mapState('event', ['eventCategories'])
  },
  methods: {
    ...mapActions('globals',['changeLoginMenuButtons'])
  }
})
</script>