
<script>


export default {

  data() {
	  return {
		wines: [
			{red_white: 'white', name: 'Chardonnay', code: 'ch', vintage: 2019, img: '', text: 'description goes here description goes here description goes here description goes here description goes here description goes here'},
			{red_white: 'white', name: 'Durant White', code: 'dw', vintage: 2019, img: '', text: 'description goes here'},
			{red_white: 'white', name: 'Pinot Gris', code: 'pg', vintage: 2019, img: '', text: 'description goes here'},
			{red_white: 'rose', name: 'Rose', code: 're', vintage: 2020, img: '', text: 'description goes here'},
			{red_white: 'red', name: 'Cabernet Franc', code: 'cf', vintage: 2019, img: '', text: 'Normally a blending grape, this varietal is very popular in Virginia and makes for a unique red wine with plenty of red-fruit, spice, and a smooth finish'},
			{red_white: 'red', name: 'Merlot', code: 'me', vintage: 2018, img: '', text: 'description goes here'},
			{red_white: 'red', name: 'Durant Red', code: 'dr', vintage: 2018, img: '', text: 'description goes here'},
			{red_white: 'red', name: 'Petit Verdot', code: 'pv', vintage: 2018, img: '', text: 'description goes here'},
		],
		links: [
			{name: 'shop', bColor: 'white', tColor: 'red', url: 'http://pollakvineyards.com/wines', text: 'Shop'},
			{name: 'info', bColor: 'white', tColor: 'red', url: 'http://pollakvineyards.com', text: 'Info'},
			{name: 'club', bColor: 'white', tColor: 'red', url: 'http://pollakvineyards.com/wines/wine-club', text: 'Wine Club'}
			]
		}
	  },
	  methods: {
	  	linkHandle() {
	  	console.log('yup')
	  		window.location.href = "http://www.w3schools.com"
	  		
	  	}
	  }
	  

}


</script>



<template>

  <z-view label="" label-pos="top" class="mode-dark theme-white">
<!--   <h4>Pollak Vineyards</h4> -->
  <img src="../assets/plogo.png" alt="logo">
  <p>Interactive Tasting</p>
  <br>
  <p style="font-size: 18px; text-decoration: italic;">Explore each of our estate-grown wines on the right, and learn more about us on the left.</p>
<!--   <img src="https://storage.googleapis.com/cdn.vinoshipper.com/winery/473/311dac8d-98a5-484e-97f0-e16afad94ac1.jpg"> -->
  
    <div slot="extension">
    
     <!-- wines -->
      <z-spot
      	v-for="(wine, index) in wines"
      	class="wine_spot"
      	propsy="props yo"
      	:ref="wine.code"
        :wine="wine"
      	:id="wine.red_white"
      	:key="index"
        :angle="270 + (200 / wines.length * index)"
        size="m"
        :distance="130"
        label=""
        label-pos="right"
        :to-view= 'wine.code'
        >
        {{wine.name}}
      </z-spot>
    
      <!-- links -->
      <z-spot
        v-for="(link, index) in links"
		:key=index
        style="background-color: orange; border-width: 4px; border-color: var(--background-color);"
        @click="linkHandle"
        :angle="210 + (-90 / links.length * index)"
        button
        size="m"
        :distance="130"
        >
<!--         <i style="color: var( ~~accent-text-color)" class="fas fa-shopping-bag"></i> -->
       <span style="color: var( --accent-text-color)">{{ link.text }}</span>
      </z-spot> 
      
    </div>
  </z-view>
  
</template>



<style>

	.wine_spot {font-size: 16px;}
	#red {background: darkred; color: white;}
	#white {background: gold; color: black;}
	#rose {background: pink; color: black;}

</style>




