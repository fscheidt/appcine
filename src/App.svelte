<script>
  import Movie from './lib/Movie.svelte'
  import User from './lib/User.svelte'
  import Person from './lib/Person.svelte'
  let menu = 1;
</script>

<main class='container'>
    <p>Pycine App</p>
    
    <ul class="nav">
        <li><a href="/" on:click|preventDefault={() => (menu = 1)}>Users</a></li>
        <li><a href="/" on:click|preventDefault={() => (menu = 2)}>Movies</a></li>
        <li><a href="/" on:click|preventDefault={() => (menu = 3)}>Artista</a></li>
    </ul>

    <div class="card">
    {#if menu === 1}
        <User/>
    {:else if menu === 2}
        <Movie/>
    {:else if menu === 3}
        <Person/>
    {:else}
        <p>invalid option</p>
    {/if}
    </div>
</main>

<style>
.container{
    /* background: #cccccc29; */
}
ul.nav {
    display: flex;
    padding: 0;
    place-content: center;
}
ul.nav li{
    display: inline-block;
    padding: 0px 5px;
}
</style>