<style scoped>
	.item-surah {
		padding-top: 5rem;
	}
	.nama-arab {
		direction: rtl;
		color: #1c3a6e !important;
		font-size: 35px;
	}
	.nama-latin {
		color: #1c3a6e;
	}
	.card {
		margin-bottom: 20px;
		border: none;
	}
</style>

<template>

	<nav class="navbar bg-white fixed-top">
		<div class="container-fluid">
			<a class="navbar-brand">Alquran</a>
			<form class="d-flex" role="search" v-on:submit.prevent>
				<input v-model="keyword" class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
				<button @click="filterSearch()" class="btn btn-outline-success">cari</button>
			</form>
		</div>
	</nav>


	<div class="container">
	<div class="row item-surah">
		<div class="col-md-4" v-for="alquranId in alquran" :key="alquranId.id">
			<div class="card">
				<div class="card-body">
					<router-link v-bind:to="/surah/+alquranId.nomor" class="text-decoration-none">
					<h5 class="nama-latin">{{ alquranId.nomor }}. {{ alquranId.nama_latin }}</h5>
					</router-link>

					<p>{{ alquranId.arti }}</p>

					<router-link v-bind:to="/surah/+alquranId.nomor" class="text-decoration-none">
					<h4 class="nama-arab">{{ alquranId.nama }}</h4>
					</router-link>
				</div>
			</div>
		</div>
	</div>	
	</div>
</template>

<script type="text/javascript">
	import axios from 'axios';

	export default {
		name: 'Item',
		data() {
			return {
				alquran: null,
				keyword: ""
			}
		},
		methods: {
		   filterSearch () {
		    const titleFilterAyat = this.keyword.toUpperCase();
		    const titleAyat = document.getElementsByTagName('h5')
		    for(let i = 0; i < titleAyat.length; i++) {
		    	const titleTextAyat = titleAyat[i].innerText || titleAyat[i].textContent;
		    	if (titleTextAyat.toUpperCase().indexOf(titleFilterAyat) > -1) {
		    		titleAyat[i].closest(".card").style.display = ""
		    	} else {
		    		titleAyat[i].closest(".card").style.display ="none"
		    	}
		    }
		  }
		},
		mounted() {
			if (localStorage.getItem('namaSurah')) {
				try {
					this.namaSurah = JSON.parse(localStorage.getItem('namaSurah'));
				} catch(e) {
					localStorage.removeItem('namaSurah');
				}
			}
			// eslint-disable-next-line
			axios.get('https://equran.id/api/surat')
			.then((data) => {
				this.alquran = data.data
			})
		}
	}
</script>


