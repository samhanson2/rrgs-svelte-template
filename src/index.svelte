<script>
let name ='World'
let text =''
</script>

<style>
</style>
<h1>Svelte</h1>

<p>Welcome to coding with Svelte!</p>
<br>
<br>
<h1 class='title'>Hello World</h1>
<p>Hello {name} </p>

<br>
<br>
<br>

<h1 class='title'>The Repeater</h1>
<p>Write something</p>
<input bind:value={text}>

<p>you wrote: {text} </p>
