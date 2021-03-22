<template>
	<div id="gif-list">
		<Gif 
			v-for="gif in gifs" 
			:key="gif.id" 
			:gif="gif"
		/>
	</div>
</template>

<style scoped>
#gif-list {
	display: flex;
	flex-wrap: wrap;
	justify-content: space-between;
}
</style>

<script>
import Gif from './Gif.vue'
export default {
	components: { Gif },
	props: {
		gifs: Array
	}
}
</script>


