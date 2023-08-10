<script>
  import Nav from "./Nav.svelte";
</script>

<header>
  <h1><a href="/">Globe</a></h1>
  <Nav />
</header>

<style>
  header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    height: 88px;
  }
  h1 {
    font-family: var(--oswald);
    font-size: 32px;
  }
</style>
