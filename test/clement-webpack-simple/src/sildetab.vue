<template>
	<ul class='sildeUl' @click='changed'>
		<li v-for='i in allImage' :style='{backgroundImage:"url("+i+")",backgroundSize:"cover"}' :class='allClass[$index]'></li>
	</ul>
</template>

<script>
export default {
	props:['silde'],
	data(){
		return {
			allImage:[],
			allClass:[]
		}
	},
	methods:{
		changed(){
			this.allClass.push(this.allClass.shift());
		}
	},
	ready(){
		this.allImage = this.silde.image;
		for(var i = 0;i<this.allImage.length;i++){
			this.allClass.push('s'+i);
		}
	}
}
</script>

<style>
	.sildeUl{height:300px;position: relative;}
	.sildeUl li{width:400px;height:200px;position: absolute;left: 50%;top:100px;transition:.5s;transform: perspective(800px);}
	.sildeUl .s0{transform: perspective(800px) translateX(25%);z-index: 2;opacity: 0}
	.sildeUl .s1{transform: perspective(800px) rotateY(-40deg);z-index: 3;opacity: 0.5}
	.sildeUl .s2{transform: perspective(800px) translateX(-25%) rotateY(-20deg);z-index: 4;opacity: 0.8}
	.sildeUl .s3{width:450px;height:250px;transform: translateX(-50%) translateY(-10%);z-index: 5;}
	.sildeUl .s4{transform: perspective(800px) translateX(-75%) rotateY(20deg);z-index: 4;opacity: 0.8}
	.sildeUl .s5{transform: perspective(800px) translateX(-100%) rotateY(40deg);z-index: 3;opacity: 0.5}
	.sildeUl .s6{transform: perspective(800px) translateX(-125%);z-index: 2;opacity: 0}
</style>