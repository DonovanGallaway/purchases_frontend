<script>
    import {Link} from 'svelte-navigator'
</script>

<style>
    nav{
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .nav-links{
        display: flex;
        width: 50%;
        justify-content: space-around;
    }
</style>

<nav>
    <h1>EPO App</h1>
    <div class="nav-links">
        <Link to="/"><button class="nav-text">Pending Purchases</button></Link>
        <Link to="instructions"><button class="nav-text">Instructions</button></Link>
        <Link to="new"><button class="nav-text">New Purchase</Link>
    </div>
</nav>