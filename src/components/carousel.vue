<template>
	<div @mouseover="clearInv()" @mouseout="runInv()">
		<ul class="imgList">
			<li class="prev" @click="prev()">&gt;</li>
			<li>
				<transition name="slide-trans">
					<img :src="imgList[activeIndex].src" v-if="isShow">
				</transition>
				<transition name="slide-trans-old">
		          <img v-if="!isShow" :src="imgList[activeIndex].src">
		        </transition>
			</li>
			<li class="next" @click="next()">&lt;</li>
		</ul>
		<ul class="slidePages">
			
			<li v-for="(img,index) in imgList" class="slideBtn" @click="goTo(index)" :class="{'activeColor':index==activeIndex}"></li>
			
		</ul>
	</div>
</template>

<script type="text/javascript">
	export default{
		data(){
			return {
				imgList:[
					{
			          src: require('../assets/slideShow/1.jpg'),
			          title: 'xxx1',
			        },
			        {
			          src: require('../assets/slideShow/2.jpg'),
			          title: 'xxx2',
			        },
			        {
			          src: require('../assets/slideShow/3.jpg'),
			        },
			        {
			          src: require('../assets/slideShow/4.jpg'),
			          title: 'xxx4',
			        },
			        {
			          src: require('../assets/slideShow/5.jpg'),
			          title: 'xxx5',
			        }
				],
				isShow:true,
				activeIndex:0,
				timer:null
			}	
		},
		mounted:function(){
			this.autoPlay();
		},
		methods:{
			goTo(index){
				this.activeIndex=index;
			},
			prev(){
				if(this.activeIndex==0){
					this.activeIndex=this.imgList.length-1;
				}else{
					this.activeIndex--;
				}
			},
			next(){
				if(this.activeIndex==this.imgList.length-1){
					this.activeIndex=0;
				}else{
					this.activeIndex++;
				}
				
			},
			autoPlay(){
				this.timer=setInterval(()=>{
					this.next();
				},3000)
			},
			clearInv(){
				clearInterval(this.timer);
				this.timer=null;
			},
			runInv(){
				this.autoPlay()
			}
		}
	}
</script>
<style type="text/css" scoped>
	.slide-trans-enter-active {
	  transition: all .5s;
	}
	.slide-trans-enter {
	  transform: translateX(500px);
	}
	.slide-trans-old-leave-active {
	  transition: all .5s;
	  transform: translateX(-500px);
	}
	li{
		list-style: none;
	}
	div{
		height: 400px;
		margin:0 auto;
		position: relative;
	}
	.imgList{
		height: 375px;
		position: relative;
	}
	img{
		width: 500px;
		height: 375px;
		position: absolute;
		top: 0;
		left: 25%;
	}
	.slidePages{
		height: 20px;
		position: absolute;
		right: 100px;
		bottom:10px;
	}
	.slideBtn{
		width: 15px;
		height: 15px;
		float: left;
		margin:0 10px;
		background: #fff;
		border-radius: 50%;
		cursor: pointer;
	}
	.activeColor{
		background: #f00;
	}
	.prev{
		left: 250px;
	}
	.next{
		right: 100px;
		z-index: 100;
	}
	.prev,.next{
		width: 30px;
		height: 50px;
		line-height: 50px;
		font-size: 25px;
		color: #fff;
		background: rgba(0,0,0,.5);
		position: absolute;
		top: 50%;
		z-index: 100;
		cursor: pointer;
	}
	
</style>