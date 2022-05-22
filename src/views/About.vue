<template>
	<div class="container">
		<div class="about">
			<h1>This is an about page</h1>
			<ul v-for="dt of data.data">
				<p>{{dt.id}}</p>
				<p>{{dt.disease_history}}</p>
			</ul>
		</div>
	</div>
</template>

<script>
	import axios from 'axios'
	export default{
		data(){
			return{
				data:[]
			}
		},

		async created(){
			await axios.get('http://127.0.0.1:8000/api/v1/consultations', {
				headers:{
					'Authorization' : 'Bearer '+localStorage.getItem('token')
				}
			}).then(response=>{
				this.data=response.data
			}).catch(e=>{
				console.log(e)
			})
		}
	}

</script>