<script>
	import { Router, Link, Route } from "svelte-navigator";
	import Header from "./components/Header.svelte";
	import PurchaseForm from "./components/PurchaseForm.svelte";

	const url = "https://purchases-backend.herokuapp.com/"

	const getPurchases = () =>{
		console.log('working')
	}
</script>


<Router>
	<Header/>
	<Route path="/">
		<h1>This is the home Route</h1>
	</Route>
	<Route path="new" let:params>
		<PurchaseForm getPurchases={getPurchases} url={url + "purchase"}/>
	</Route>
</Router>