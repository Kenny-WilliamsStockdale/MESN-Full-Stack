<script>
	import Header from "./components/Header.svelte";
	import Footer from "./components/Footer.svelte";
	import Landing from "./pages/Landing.svelte";
	import Login from "./pages/Login.svelte";
	import Signup from "./pages/Signup.svelte";
	import Account from "./pages/Account.svelte";
	import { Router, Route } from "svelte-navigator";
</script>

<Router>
	<Header />
	<main>
		<Route path="/" component={Landing} />
		<Route path="/Login" component={Login} primary={false} />
		<Route path="/Signup" component={Signup} primary={false} />
		<Route path="/Account" component={Account} primary={false} />
	</main>
	<Footer />
</Router>

<style>
</style>
