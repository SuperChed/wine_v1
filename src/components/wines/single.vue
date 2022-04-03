

<script>

export default {
    inject: ['testy'],
	data() {
		return{
			// this passes the obj w all info. would only need to change
			  // the wine.code possibly with 
			  
			wine: this.$parent.$children[0].$refs[this.testy][0].$attrs.wine,
			// these can be lumped into the orig wines objects and accessed
			  // with dot notation in components. like   this.wine.aroma[storeVarAsIndex]
			qlty_aroma: ['cherry', 'spice', 'cassis', 'graphite'],
			aromabk: ['blue', 'red', 'green', 'orange'],
			qlty_flavor: ['bright', 'red-fruit', 'savory', 'pepper'],
			qlty_finish: ['smooth', 'oaky', 'fruit-forward', 'long-lasting'],
			// re-write with stored(Pinia) values.   aromaval: storeVar
			  // then re-write local methods using new vars
			aromaval: -1,
			flavorval: -1,
			finishval: -1
		}
	},
	mounted() {
		console.log(this.$parent.$children[0].$refs)
	},
	methods: {
		aroma() {
			if (this.aromaval < 4) {
				this.aromaval++
			}
			if (this.aromaval == 4) {
				this.aromaval = 0
			}
		},
		flavor() {
			if (this.flavorval < 4) {
				this.flavorval++
			}
			if (this.flavorval == 4) {
				this.flavorval = 0
			}
		},
		finish() {
			if (this.finishval < 4) {
				this.finishval++
			}
			if (this.finishval == 4) {
				this.finishval = 0
			}
		}
	},
	computed: { }



}

</script>

	


<template>

	<z-view style="background:white; color: black;" >
		<h4>{{ this.wine.name }}</h4>
		<p>{{ this.wine.vintage }}</p>
		<div id="inner">
			<!-- can't use var for img path?? maybe needs to be put into computed??	-->
			<img src="../../assets/skinny_btl.png" alt="bottle" >
			<p>{{ this.wine.text }}</p>
		</div>
		
		
		<div slot="extension">
		
			<z-spot
			imagePath="https://www.thewinecellarinsider.com/wp-content/uploads/2010/05/Davis-Wine-Aroma-Wheel1.jpg"
			:distance="130"
			to-view="aroma"
			:angle="210"
			>
			</z-spot>
			
			<z-spot
				imagePath="https://miro.medium.com/max/700/1*0NXOvaNILS5Hr0yYAfDyVA.png"
				:distance="130"
				to-view="palate"
				:angle="180"
			>
			</z-spot>
			
			<z-spot
			  button
			  class="wine_options"
			  :distance="130"
			  :angle="340"
			  size="m"
			>
			 <div @click="aroma" class="ohdiv" :style="{background: this.aromabk[this.aromaval]}">	
			  <p v-if="this.aromaval == -1">choose an aroma</p>
			  <p v-else>{{this.qlty_aroma[this.aromaval]}}</p>
			 </div>
			</z-spot>
			
			<z-spot
			  button
			  class="wine_options"
			  :distance="130"
			  :angle="5"
			  size="m"
			>
			<div @click="flavor" class="ohdiv" :style="{background: this.aromabk[this.flavorval]}">	
			  <p v-if="this.flavorval == -1">choose a flavor</p>
			  <p v-else>{{this.qlty_flavor[this.flavorval]}}</p>
			</div>
			</z-spot>
			
			<z-spot
			  button
			  class="wine_options"
			  :distance="130"
			  :angle="30"
			  size="m"
			>
			<div @click="finish" class="ohdiv" :style="{background: this.aromabk[this.finishval]}">	
			  <p v-if="this.finishval == -1">choose a finish</p>
			  <p v-else>{{this.qlty_finish[this.finishval]}}</p>
			 </div>
			</z-spot>
			
			
			
			
		
		</div>
		
	</z-view>




</template>




<style>

	.wine_options {font-size: 18px; overflow: hidden;}
	#inner {
		display: flex;
		width: 90%;
		margin-left: 25px;
	}
	#inner img { margin-top: -20px; }
	#inner p { margin-top: 20px; font-size: 18px; text-align: left;}

	.test{
		margin-bottom: 40px;
	}

	.ohdiv{padding: 60px;}

</style>

