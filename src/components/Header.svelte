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
        <Link to="/"><h2 class="nav-text">Pending Purchases</h2></Link>
        <Link to="instructions"><h2 class="nav-text">Instructions</h2></Link>
        <Link to="new"><h2 class="nav-text">New Purchase</Link>
    </div>
</nav>