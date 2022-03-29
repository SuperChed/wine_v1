

<script>

export default {

	data() {
		return{
			wine: this.$parent.$children[0].$refs.cf[0].$attrs.wine,

// 			name: this.$parent.$children[0].$refs.ch[0].$attrs.name,
// 			vintage: this.$parent.$children[0].$refs.ch[0].$attrs.vintage,
// 			text: this.$parent.$children[0].$refs.ch[0].$attrs.text,
// 			img: this.$parent.$children[0].$refs.ch[0].$attrs.img
			
		}
	},
	props: [],
	mounted() {
		console.log(this.wine.name)
	}



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
		<p style="width: 70%; text-align: center; margin: auto; font-size: 18px">Color - dard red with orange hue.</p>
		<p style="width: 70%; text-align: center; margin: auto; font-size: 18px">Palate - bright acidity and spice.</p>
		<p style="width: 70%; text-align: center; margin: auto; font-size: 18px">Finish - smooth long-lasting tannins</p>
		
		
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
			  class="wine_options"
			  propsy="this is a prop"
			  :distance="130"
			  to-view="color"
			  :angle="340"
			  size="m"
			>
			Color & Aroma
			</z-spot>
			
			<z-spot
			  class="wine_options"
			  :distance="130"
			  to-view="flavor"
			  :angle="5"
			  size="m"
			>
			Flavors
			</z-spot>
			
			<z-spot
			  class="wine_options"
			  :distance="130"
			  to-view="finish"
			  :angle="30"
			  size="m"
			>
			Texture & Finish
			</z-spot>
			
			
			
			
		
		</div>
		
	</z-view>




</template>




<style>

	.wine_options {font-size: 18px;}
	#inner {
		display: flex;
		width: 90%;
		margin-left: 25px;
	}
	#inner img { margin-top: -20px; }
	#inner p { margin-top: 20px; font-size: 18px; text-align: left;}


</style>

