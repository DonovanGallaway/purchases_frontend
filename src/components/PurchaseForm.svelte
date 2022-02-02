<script>
    export let formData = {
        name: "",
        cost: 0,
        link: "",
        submitted: false,
        purchased: false,
        notes: ""
    }

    // $: console.log(formData)

    export let url
    export let getPurchases
    export let method = 'post'
    
    const addPurchase = async () => {
		await fetch(url, {
			method: "post",
			headers: {
				"Content-Type": "application/json"
			},
			body: JSON.stringify(formData)
		})
        getPurchases()        
	}

    const editPurchase = async () => {
		await fetch(url, {
			method: "put",
			headers: {
				"Content-Type": "application/json"
			},
			body: JSON.stringify(formData)
		})
        getPurchases()        
	}

</script>

<style>
    h4{
        font-size: 2em;
        margin: .5em;
    }
</style>

{#if method=='post'}
<form on:submit|preventDefault={addPurchase}>
    <label for='item name'><h4>Item Name: </h4>
        <input type='text' name='name' bind:value={formData.name}/>
    </label>
    <label for='cost'><h4>Cost: </h4>
        <input type='number' name='cost' bind:value={formData.cost}/>
    </label>
    <label for='link'><h4>Link: </h4>
        <input type='text' name='name' bind:value={formData.link}/>
    </label>
    <label for='submitted'><h4>Submitted: </h4>
        <input type='checkbox' name='submitted' bind:checked={formData.submitted}/>
    </label>
    <label for='purchased'><h4>Purchased: </h4>
        <input type='checkbox' name='purchased' bind:checked={formData.purchased}/>
    </label>
    <input type='submit' value='Add Purchase Request'/>
</form>


{:else}
<form on:submit|preventDefault={editPurchase}>
    <label for='username'><h4>Username:</h4>
        <input type='text' name='username' bind:value={formData.username}/>
    </label>
    <label for='word goal'><h4>Word Goal: </h4>
        <input type='number' name='wordGoal' bind:value={formData.wordGoal}/>
    </label>
    <input type='submit' value='Edit Purchase Request'/>
</form>
{/if}
