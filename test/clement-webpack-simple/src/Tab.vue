<template>
	<div class='outNode' @mouseover='over' @mouseout='out'>
		<ul>
			<li v-for='i in allImage' :style='{background:"url("+i+") repeat",backgroundSize:cover}' :class='index=$index' v-show='needIndex==$index?true:false' transition='fade'></li>
		</ul>
		<ol class='tabHover' :style='{width:allImage.length*20+"px"}'>
			<li v-for='i in allImage' :class='needIndex==$index?"active":""' @click='needIndex=$index'></li>
		</ol>
		<div class="mini" :style='{width:allImage.length*83+"px",bottom:bottomN+"px"}'>
			<img :src="i" v-for='i in allImage' width="77" height="46" @click='needIndex=$index'>
		</div>
	</div>
</template>

<script>
export default {
	props:['tab'],
	data(){
		return {
			allImage:[],
			needIndex:'',
			bottomN:'',
			interval:''
		}
	},
	methods:{
		over(){
			this.bottomN = 0;
			clearInterval(this.interval);
		},
		out(){
			this.bottomN=-56;
			clearInterval(this.interval);
			this.interval = setInterval(()=>{
				this.needIndex++;
				this.needIndex == this.allImage.length && (this.needIndex = 0);
			},1500);
		}
	},
	ready(){
		this.allImage = this.tab.image;
		this.needIndex = this.tab.index;
		this.bottomN = this.tab.bottomNode;
		this.interval = this.tab.interval;

		clearInterval(this.interval);
		this.interval = setInterval(()=>{
			this.needIndex++;
			this.needIndex == this.allImage.length && (this.needIndex = 0);
		},1500);
	}
}
</script>

<style>
	.fade-transition{
		opacity:1;transition:.9s;
	}
	.fade-enter{
		opacity:0;
	}
	.fade-leave{
		opacity:0;
	}
	.outNode{width:495px;height:290px;position:relative;overflow:hidden;left: 50%;transform: translateX(-50%);}
	.outNode ul{width:100%;height:100%;position:absolute;}
	.outNode ul li{width:100%;height:100%;position:absolute;top:0;left:0;}
	.tabHover{height:20px;position:absolute;z-index:10;bottom:7px;left:50%;transform:translateX(-50%)}
	.tabHover li{width:6px;height:6px;background:#fff;margin:7px 7px;float:left;border-radius:50%;transition:0.8s;cursor:pointer;}
	.tabHover li.active{background:#ff0002;}
	.mini{transition:.8s;height:57px;background:rgba(255,255,255,0.7);position:absolute;z-index:11;bottom:0;left:50%;transform:translateX(-50%)}
	.mini img{float: left;margin: 4px 3px 6px;}
</style>