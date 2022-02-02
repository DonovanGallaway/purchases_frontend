<script>
	import { Router, Link, Route } from "svelte-navigator";
	import {onMount} from 'svelte'
	import Header from "./components/Header.svelte";
	import PurchaseForm from "./components/PurchaseForm.svelte";
	import Index from "./pages/Index.svelte";
import Show from "./pages/Show.svelte";

	const url = "https://purchases-backend.herokuapp.com/"
	let purchases = []

	const getPurchases = async () =>{
		const response = await fetch(url + "purchase")
		const data = await response.json()
		purchases = data
	}
    
</script>


<Router>
	<Header/>
	<Route path="/">
		<Index getPurchases={getPurchases} purchases={purchases}/>
	</Route>
	<Route path="new" let:params>
		<PurchaseForm getPurchases={getPurchases} url={url + "purchase"}/>
	</Route>
	<Route path="edit/:id" let:params>
		<PurchaseForm 
		getPurchases={getPurchases} 
		url={url + "purchase/" + params.id} 
		formData={purchases.find(x => x._id === params.id)}
		method="put"/>
	</Route>
	<Route path=":id" let:params>
		<Show getPurchases={getPurchases} purchases={purchases} purchaseId={params.id}/>
	</Route>
</Router>