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
</style>

<template>
	<div class="container">
	<div class="row item-surah">
		<div class="col-md-4" v-for="alquranId in alquran" :key="alquranId.id">
			<div class="card mb-4 border-0">
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
	import axios from 'axios'
	let namaSurah;
	export default {
		name: 'Item',
		data() {
			return {
				alquran: null
			}
		},
		methods: {
		  getNama(keyName) {
		    const nama = keyName
		    for(this.namaLatin of nama) {
		    	// console.log(this.namaLatin.nama_latin)
		    	return namaSurah = this.namaLatin.nama_latin
		    }
			console.log(namaSurah)
		  }
		},
		mounted() {
			// eslint-disable-next-line
			axios.get('https://equran.id/api/surat')
			.then((data) => {
				this.alquran = data.data
				this.getNama(this.alquran)
			})
		}
	}
</script>


