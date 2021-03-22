<template>
	<div class="inputs">
		<input
			class="search"
			placeholder="Type something to search"
			@input="handleInput"
			v-model="keyword"
		>
		<input
			class="limit"
			type="number"
			placeholder="Limit"
			v-model="limit"
		>
	</div>
</template>

<script>
export default {
	data() {
		return {
			api_key: 'p8UGZz2v15uR4SOCpy6NJ40KiCsTk1KG',
			keyword: '',
			limit: 9,
			timeout: null,
		}
	},
	methods: {
		handleInput() {
			clearTimeout(this.timeout)
			this.timeout = setTimeout(() => this.search(),500)
		},
		search() {
			fetch(`https://api.giphy.com/v1/gifs/search?api_key=${this.api_key}&limit=${this.limit}&q=${this.keyword}`)
				.then(res => res.json())
				.then(data => {
					this.gifs = data.data
					this.$emit('gifsFetched',this.gifs)
				})
		}
	}
}
</script>


<style scoped>
.inputs {
	display: flex;
	width: 100%;
	margin-bottom: 20px;
    justify-content: space-between;
}
.search {
	width: 80%;
}
.limit {
	width: 19%;
}
input {
	outline: none;
	padding: 10px;
	border: 1px solid #3e329c;
	border-radius: 2px;
}
input:focus {
	outline: 2px solid #2c1abd;
}
</style>