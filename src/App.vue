

<template>
  <z-canvas :views='$options.components' style="background-color: white; background-image: url('https://websnoot.com/vineyard-map/tasting1.jpg'); background-position: center; background-repeat: no-repeat; background-size: cover;"></z-canvas>
</template>



<script>

import home from './components/home'
import palate from './components/palate'
import finish from './components/finish'
import aroma from './components/aroma'

import ch from './components/wines/chardonnay'
import dw from './components/wines/durant_white'
import pg from './components/wines/pinot_gris'
import re from './components/wines/rose'
import cf from './components/wines/cab_franc'
import me from './components/wines/merlot'
import dr from './components/wines/durant_red'
import pv from './components/wines/petit_verdot'
import single from './components/wines/single'

export default {

  components: {
    home, palate, finish, aroma, dw, ch, pg, re, cf, me, dr, pv, single
  },
  mounted () {
    this.$zircle.setView('home')
  },
  provide: function() {
    return {
      testy: 'cf'
    }
  }
}

</script>


<style>
@import url('https://fonts.googleapis.com/css?family=Source+Sans+Pro:400,700');
@import url('https://use.fontawesome.com/releases/v5.1.0/css/all.css');
</style>