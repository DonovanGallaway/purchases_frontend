<script>
    import {onMount} from 'svelte'
    import {Link} from 'svelte-navigator'

    export let getPurchases
    export let purchaseId
    export let purchases

    let purchase = {}

    onMount(()=>{
        getPurchases()
        purchase = purchases.find(x => x._id === purchaseId)
    })
</script>


<h1>{purchase.name}</h1>
<h2>{purchase.cost}</h2>
<a href={purchase.link}><h2>Link</h2></a>
<h2>Submitted? {purchase.submitted ? "Yes" : "No"}</h2>
<h2>Purchased? {purchase.purchased ? "Yes" : "No"}</h2>
<p>{purchase.notes}</p>

<Link to={`/edit/${purchase._id}`}><button>Edit</button></Link>