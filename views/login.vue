<template>
	<main>
    <form class="box">
      <p if="err_message" class="err_message">{{err_message}}</p>
			<img src="https://malcoded.com/static/713b40a34ef44b9c6180fa626bf45937/6ff5e/nodejs-cli-banner.png" alt="">
      <div class="input-box">
        <label for="iEmail">e-mail</label>
        <input v-model="vEmail" name="iEmail" type="email" placeholder="enter your e-mail" />
      </div>
      <div class="input-box">
        <label for="iPassword">password</label>
        <input v-model="vPassword" name="iPassword" type="password" placeholder="enter your password" />
      </div>
      <button @submit.prevent="login">Submit</button>
      <div class="footer-box">
        <p><strong>All rights reserved</strong></p>
        <p>&copy; Deyvison Borges - 2020</p>
      </div>
    </form>
  </main>
</template>

<script>
export default {
	name: 'ViewLogin',
	data () {
		return {
			err_message: null,
			vEmail: null,
			vPassword: null
		}
	},
	methods: {
		async login() {
			try {
				console.log(this.err_message)
				console.log('passei por aqiu')
				await this.$store.dispatch('login', {
					email: this.vEmail,
					password: this.vPassword
				});
			} catch (err) {
				this.err_message = err;
				return;
			}
		}
	},
}
</script>

<style scoped>
.err_message {
	color: #df2c2c;
	font-size: 0.9rem;
	margin: 10px 0;
	padding: 5px;
	position: relative;
	text-align: center;
}
main {
	background-color: #363a45;
	display: grid;
	grid-template-columns: 1fr auto 1fr;
	grid-template-rows: 1fr auto 1fr;
	grid-template-areas:
		"top     top     top"
		"lside   center  rside"
		"bottom  bottom  bottom";
	grid-auto-flow: column;
	height: 100vh;
}

.box {
	display: grid;
	grid-column: 2/3;
	grid-row: 2/3;
}

.input-box {
	display: grid;
	grid-auto-flow: row;
	grid-auto-rows: auto;
	grid-template-columns: 1fr;
	margin: 20px 0;
	position: relative;
}

.input-box label {
	color: #ffffff93;
	font-size: 0.9rem;
	font-weight: bold;
	position: relative;
	text-transform: uppercase;
}

.input-box input {
	background: none;
	border: none;
	border-bottom: 1px solid #a9a9a9;
	color: #a9a9a9;
	font-size: 1.1rem;
	outline: none;
	padding: 10px 0;
	position: relative;
	width: 100%;
}

.input-box input:focus {
	font-weight: 700;
}

.footer-box {
	color: #9aa4a7;
	display: grid;
	grid-auto-flow: row;
	grid-auto-rows: auto;
	grid-template-columns: 1fr;
	margin: 10px 0;
	position: relative;
	text-align: center;
}

button {
	background-color: #679e63;
	border: none;
	border-radius: 8px;
	box-shadow: 0 0 5px 0 #50894a;
	color: #363a45;
	display: grid;
	font-size: 1.1rem;
	font-weight: bold;
	margin: 5px 0;
	padding: 15px 20px;
	position: relative;
	width: 100%;
}

button:hover {
	cursor: pointer;
}

img {
	width: 300px;
	height: auto;
}
</style>
