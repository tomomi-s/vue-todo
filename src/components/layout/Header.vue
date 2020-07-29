<template>
	<div>
		<h1 class="header">Todo List</h1>
		<div id="nav">
			<router-link to="/">Home</router-link> |
			<router-link to="/about">About</router-link>
		</div>
	</div>
</template>

<script>
	export default{
		name: "Header"
	}
</script>

<style scoped>
	.header{
		text-align: center;
	}

	#nav {
		padding: 30px;
		text-align: center;
	}

	#nav a {
		font-weight: bold;
		color: #2c3e50;
		text-decoration: none;
	}

	/*#nav a.router-link-exact-active {
		color: #42b983;
	}*/
</style>