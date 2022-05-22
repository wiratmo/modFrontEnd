<template>
	<input type="text" name="username" placeholder="username" ref="username">
	<input type="password" name="password" placeholder="password" ref="password">
	<input type="submit" name="kirim" value="KIRIM" @click="postData">
	{{login}}
</template>

<script>
	import axios from 'axios'

	export default{
		data(){
			return {
				login:[]
			}
		},
		methods:{
			async postData(){
				axios.post("http://127.0.0.1:8000/api/v1/auth/login", {
					headers :{
						'Accept': 'application/json'
					},
					/*data*/
					id_card_number: this.$refs.username.value,
					password: this.$refs.password.value
					
				}).then(response=>{
					this.login = "login anda berhasil"
					localStorage.setItem('token', response.data.token)
				}).catch(e=>{
					console.log(e)
				})
			}
		}
	}
</script>
