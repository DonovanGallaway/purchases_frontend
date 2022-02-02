<script>
    import {Link} from 'svelte-navigator'


    export let purchases
    export let requester
    $: unsubmitted = purchases.filter(x => !x.submitted && !x.purchased)
    $: submitted = purchases.filter(x => x.submitted && !x.purchased)
    $: purchased = purchases.filter(x => x.purchased)
</script>

<h2>{requester}'s Unsubmitted Purchase Requests</h2>
{#each unsubmitted as purchase}
    <Link to={`/${purchase._id}`}>
        <h3>{purchase.name} - ${purchase.cost}</h3>
    </Link>
{/each}
<h2>Submitted Purchase Requests</h2>
{#each submitted as purchase}
    <Link to={`/${purchase._id}`}>
        <h3>{purchase.name} - ${purchase.cost}</h3>
    </Link>
{/each}
<h2>Purchased Items</h2>
{#each purchased as purchase}
    <Link to={`/${purchase._id}`}>
        <h3>{purchase.name} - ${purchase.cost}</h3>
    </Link>
{/each}