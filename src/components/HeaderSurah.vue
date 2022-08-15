<template>
	
	<nav class="navbar navbar-expand-lg bg-white fixed-top">
		<div class="container-fluid">
			<a class="navbar-brand" href="#">Navbar</a>
			<button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
				<span class="navbar-toggler-icon"></span>
			</button>
			<div class="collapse navbar-collapse" id="navbarNav">
				<select class="form-select" aria-label="Default select example">
					<option v-for="surahAll in surah" v-bind:key="surahAll.id">{{ surahAll.nama_latin }}</option>
				</select>
			</div>
		</div>
	</nav>

</template>

<script type="text/javascript">
	import axios from 'axios';

	export default {
		name: 'HeaderSurah',
		data() {
			return {
				surah: []
			}
		},
		mounted() {
			axios.get('https://equran.id/api/surat')
				.then((surahAll) => this.surah = surahAll.data)
		}
	}
</script>