<template>
  <v-flex xs12 sm6 lg4 xl3 class="text-xs-center portfolio-item">
    <v-card>
      <!-- Image -->
      <v-card-media :src="'/portfolio/' + img" height="200px"/>

      <!-- Title -->
      <v-card-title primary-title>
        <div>
          <h3 class="headline mb-0">{{ name }}</h3>
        </div>
      </v-card-title>

      <!-- Actions -->
      <v-card-actions>
        <v-btn flat color="blue darken-2" :href="link" :disabled="!link" target="_blank">{{ link? 'Acessar' : 'Não disponível' }}</v-btn>
        <v-spacer/>
        <v-btn icon @click.native="show = !show">
          <v-icon>{{ show ? 'keyboard_arrow_up' : 'keyboard_arrow_down' }}</v-icon>
        </v-btn>
      </v-card-actions>

      <!-- Description -->
      <v-slide-y-transition>
        <v-card-text v-show="show" class="text-xs-left">
          <slot/>
        </v-card-text>
      </v-slide-y-transition>
    </v-card>

  </v-flex>
</template>

<style>
  .portfolio-item {
    padding: 0 10px 25px 10px;
  }
</style>

<script>
  export default {
    props: ['name', 'img', 'link'],
    data () {
      return {
        show: false
      }
    }
  }
</script>