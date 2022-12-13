<script>
let person_id = null;
let person = null;
let message = null;
async function getPerson() {
    const res = await fetch(
        `http://localhost:8000/artista/id/${person_id}`
    );
    const data = await res.json();
    if (res.ok) {
        person = data;
        message = null;        
    } else {
        person = null;
        message = `ID ${person_id} ${res.statusText}`;
    }
}
</script>

<input bind:value={person_id} type="text" placeholder="person ID: 1100">
<button on:click={getPerson}>
find
</button>

<div class="table">
    {#if person !== null}
        <p>{person.id}</p>        
        <p>{person.name}</p>        
        <p>{person.popularity}</p>        
        <p class='desc'>{person.biography}</p>        
    {:else if message !== null}
        <p class='error'>{message}</p>
    {/if}
</div>

<style>
.error{
    color: #e35a5a;
}
.table{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    border: 1px solid #ccc;
    padding: 10px;
}
.table .desc{
    color: #646cff;
    grid-column: 1/4;
}
</style>