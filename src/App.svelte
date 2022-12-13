<script>
  import Movie from './lib/Movie.svelte'
  import User from './lib/User.svelte'
</script>

<main>
  <p>Pycine App</p>

  <div class="card">
    <User/>
  </div>

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