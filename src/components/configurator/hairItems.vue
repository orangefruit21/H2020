<template>
	<section class="items" :class="[{scrollM:items.length >=1},{scrollD:items.length >=11}]">
		<button class="button"
			v-for="item in items"
			v-bind:key="item.id"
			v-on:click="drawOnCanvas(item)">
			<img :src="item.src" alt="">
		</button>
	</section>
</template>

<script>
export default {
	props: ['items','type'],
	name:'hairitems',
	methods:{
		drawOnCanvas(elem){
			this.$store.dispatch('PUSH_'+this.type, elem)

		}
	}
}
</script>

<style scoped>
	.items{
		display: flex;
		justify-content: flex-start;
		flex-wrap: nowrap;
		padding-left: calc(var(--vh, 1vh) * 0.5);
		padding-top: calc(var(--vh, 1vh) * 0.3);
		overflow: hidden;
		height: 45vw;
	}
	.scrollM{
		overflow-x: scroll;
	}
	.button{
		width: 35vw;
		height: calc(var(--vh, 1vh) * 18.8);
		border-radius: 1vw;
		cursor: pointer;
		transition: 0.5s;
		background: linear-gradient(rgb(130, 255, 136), rgb(140, 242, 255));
		border: none;
		margin-right: calc(var(--vh, 1vh) * 0.4);
		margin-top: calc(var(--vh, 1vh) * 0.1);
		flex-shrink: 0;
	}
	.button::-moz-focus-outer{
		border: none;
	}
	.button:hover {
		transform: scale(1.05);
		background: none;
		transition: 0.3s;
	}
	.button:focus {
		border: 0.1vw solid #ac40f1;
	}
	.button:nth-of-type(3) img{
    height: initial;
    width: 80%;
	}
	.button:nth-of-type(6) img{
		height: initial;
		width: 70%;
	}
	.button:nth-of-type(8) img{
		height: initial;
		width: 80%;
	}
	img{
		height: 60%;
	}
	@media screen and (min-width: 760px) and (max-width: 999px) {
	}
	@media screen and (min-width: 1000px), (orientation: landscape){
		.items{
			flex-wrap: wrap;
			justify-content: space-around;
			height: 20.5vw;
		}
		.button{
			width: 9.4vw;
			height: 8.9vw;
			margin-top: 0vw;
			flex-shrink: initial;
			margin: 0vw;
			margin-top: calc(var(--vh, 1vh) * 0.9);
			margin-right: 0.1vw;
		}
		.button:nth-of-type(3) img{
			height: initial;
			width: 80%;
		}
		img{
			height: 60%;
		}
		.scrollD{
			overflow-y: scroll;
		}
		.scrollM{
			overflow-x: hidden;
		}
	}
	@media screen and (max-width: 999px) and (orientation: landscape){
		.items{
			flex-wrap: nowrap;
			justify-content: flex-start;
		}
		.scrollD{
			overflow-y: hidden;
		}
		.scrollM{
			overflow-x: scroll;
		}
		.button{
		width: 8vw;
		height: calc(var(--vh, 1vh) * 18.8);
		border-radius: 1vw;
		cursor: pointer;
		transition: 0.5s;
		background: linear-gradient(rgb(130, 255, 136), rgb(140, 242, 255));
		border: none;
		margin-right: 1vw;
		margin-top: calc(var(--vh, 1vh) * 0.1);
		flex-shrink: 0;
	}
	img{
		height: 55%;
	}
	}
</style>