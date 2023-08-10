<script>
  import NarrowNav from "./NarrowNav.svelte";
</script>

<header>
  <h1 class="logo"><a href="/">Globe</a></h1>
  <NarrowNav />
</header>

<style>
  header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    height: 10dvh;
    padding: 0 24px;
  }
  .logo {
    font-family: var(--oswald);
    font-size: 32px;
    color: var(--secondary-color);
  }
</style>
