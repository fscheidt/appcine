<script>
  import Movie from './lib/Movie.svelte'
</script>

<main>
  <p>Pycine App</p>

  <div class="card">
    <Movie/>
  </div>

  <button>button</button>

</main>

<style>
/* main :global(button){ */
main button{
    color: rgb(255, 0, 179);
}
button{
    color: rgb(78, 65, 74);
}
</style>