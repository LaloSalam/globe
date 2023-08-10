<script>
  import Nav from "./Nav.svelte";
  import HeaderCta from "./HeaderCta.svelte";
</script>

<header>
  <h1><a href="/">Globe</a></h1>
  <div class="nav_and_cta">
    <Nav />
    <HeaderCta />
  </div>
</header>

<style>
  header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    height: 88px;
    padding: 0 96px;
  }
  h1 {
    font-family: var(--oswald);
    font-size: 32px;
    color: var(--secondary-color);
  }
  .nav_and_cta {
    display: flex;
    align-items: center;
    gap: 24px;
    height: 100%;
  }
</style>
