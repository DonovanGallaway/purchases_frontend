<script>
    import {onMount} from 'svelte'
    import {Link} from 'svelte-navigator'

    export let getPurchases
    export let purchases
    $: pendingPurchases = purchases.filter(x =>{
        return !x.purchased
    })
    $: completedPurchases = purchases.filter(x =>{
        return x.purchased
    })


    onMount(()=>{
        getPurchases()
    })
</script>

<h1>Pending Purchases</h1>
{#each pendingPurchases as purchase}
    <Link to={purchase._id}>
        <h3>{purchase.name} - ${purchase.cost}</h3>
    </Link>
{/each}

<h1>Completed Purchases</h1>
{#each completedPurchases as purchase}
    <Link to={purchase._id}>
        <h3>{purchase.name} - ${purchase.cost}</h3>
    </Link>
{/each}