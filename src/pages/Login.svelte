<script>

    export let url
    let form = {
        username: "",
        password: ""
    }

const handleSubmit = async ()=>{
    const {username, password} = form
    const response = await fetch(`${url}`, {
        method: "post",
        headers: {
            "Content-Type": "application/json"
        },
        body: JSON.stringify({username, password})
    })
    const data = await response.json()
    return data
}

</script>
<form on:submit|preventDefault>
    <input type="text" name="username" bind:value={form.username} placeholder="Username"/>
    <input type="password" name="password" value={form.password}/>
    <input type="submit" value="Login"/>
</form>