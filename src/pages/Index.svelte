<script>
    import {onMount} from 'svelte'
    import {Link} from 'svelte-navigator'
import { each } from 'svelte/internal';

    export let getPurchases
    export let purchases
    $: pendingPurchases = purchases.filter(x =>{
        return x.submitted && !x.purchased
    })
    $: completedPurchases = purchases.filter(x =>{
        return x.purchased
    })
    $: requesters = [...new Set(purchases.map(x => x.requester))]
    


    onMount(()=>{
        getPurchases()
    })
</script>

<h3>Submitted Purchases</h3>
{#each pendingPurchases as purchase}
    <Link to={purchase._id}>
        <h3>{purchase.name} - ${purchase.cost}</h3>
    </Link>
{/each}

<h3>Completed Purchases</h3>
{#each completedPurchases as purchase}
    <Link to={purchase._id}>
        <h3>{purchase.name} - ${purchase.cost}</h3>
    </Link>
{/each}

<h3>Requests by User</h3>
{#each requesters as requester}
    <Link to={`requester/${requester}`}>
        <h3>{requester}</h3>
    </Link>
{/each}