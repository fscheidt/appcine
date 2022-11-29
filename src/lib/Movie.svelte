<script>
let promise = getMovies();
async function getMovies() {
    const res = await fetch(
        `http://localhost:8000/movies`
    );
    const text = await res.json();
    if (res.ok) {
        return text;
    } else {throw new Error(text); }
}
function handleClick() {
    promise = getMovies();
}
</script>
<button on:click={handleClick}>
list movies
</button>

<!--
    get from endpoint /genres
    <select>
        <option>Drama</option>
    </select
-->

{#await promise}
<p>...waiting</p>
{:then movies}

<div class="table">
    {#each movies as m }
        <p><img src="{m.poster_path}"/></p>
        <!-- <p>{m.id}</p> -->
        <p>{m.title}</p>
        <p>{m.genres}</p>
        <!-- TODO: salvar filme como favorito -->
        <p>Save</p>
    {/each}
</div>

{:catch error}
    <p style="color: red">{error.message}</p>
{/await}

<style>
.table{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr min-content;
    border: 1px solid #ccc;
    padding: 10px;
}
</style>