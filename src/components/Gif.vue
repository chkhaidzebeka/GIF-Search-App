<template>
	<div :style="`background-image: url(${ gif.images.fixed_height_small.url })`" class="gif">
		<div class="link">
			<input ref="url" readonly type="text" :value="gif.images.original.url">
			<button @click="copyUrl">Copy</button>
		</div>
	</div>
</template>

<style>
.gif {
	width: 240px;
	height: 240px;
	background-repeat: no-repeat;
	background-size: cover;
	background-position: center;
	margin-bottom: 10px;
	justify-content: space-between;
	position: relative;
}

.link {
	position: absolute;
	bottom: 0px;
	display: flex;
	justify-content: space-between;
	width: 100%;
}

.link input	{
	border: none;
	outline: none;
	width: 100%;
	background: #e2e2e275;
	color: #212020;
}

.link button {
	border: none;
	outline: none;
    background: #0984e3;
    padding: 5px 2px;
    border-radius: 2px;
    color: #ececec;
    cursor: pointer;
}

@media screen and (max-width: 480px) {
	.gif {
		width: 100%;
	}
	body {
		margin: 10px;
	}
}
</style>

<script>
export default {
	props: {
		gif: Object
	},
	methods: {
		copyUrl() {
			this.$refs.url.select();
			document.execCommand('copy')
			this.$refs.url.value = 'Copied!'
		}
	}
}
</script>


