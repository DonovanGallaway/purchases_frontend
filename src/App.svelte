<script>
	import { Router, Link, Route, useParams } from "svelte-navigator";
	import {onMount} from 'svelte'
	import Header from "./components/Header.svelte";
	import PurchaseForm from "./components/PurchaseForm.svelte";
	import Index from "./pages/Index.svelte";
	import Show from "./pages/Show.svelte";
import Requester from "./pages/Requester.svelte";

	const url = "https://purchases-backend.herokuapp.com/"
	let purchases = []
	let token
	let username
	let userId

	const getPurchases = async () =>{
		const response = await fetch(url + "purchase")
		const data = await response.json()
		purchases = data
	}

	const getToken = (tokenProp) =>{
		token = tokenProp
		localStorage.setItem("token", JSON.stringify(token))
	}
    
</script>

<style>
	main{
		text-align: center;
	}
</style>

<Router>
	<Header/>
	<main>
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
	<Route path="requester/:name" let:params>
		<Requester purchases={purchases.filter(x => {return x.requester === params.name})} requester={params.name}/>	
	</Route>
	<Route path="instructions">
		<h2>This is a WIP</h2>
	</Route>
	<Route path=":id" let:params>
		<Show getPurchases={getPurchases} purchases={purchases} purchaseId={params.id} url={url + "purchase/" + params.id}/>
	</Route>
</main>
</Router>