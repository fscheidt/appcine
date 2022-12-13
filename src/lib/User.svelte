<script>
let resposta = "";
async function sendForm(e){
    // envia o formulario no formato json
    let formData = new FormData(e.target);
    let data = Object.fromEntries(formData.entries());
    const res = await fetch('http://localhost:8000/user/create',{
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify(data)
    });
    const json = await res.json();
    resposta = JSON.stringify(json);
}
</script>

<h2>New user</h2>

<p>{resposta}</p>

<form class="crud" on:submit|preventDefault={sendForm}>
    <input type="text" name="name" placeholder="User name">
    <input type="text" name="email" placeholder="Email">
    <input type="text" name="password" placeholder="password">
    <input type="submit" value="add">
</form>

<style>
form.crud{
    display: grid;
    grid-template-columns: 1fr;
    gap: 5px;
}
</style>
