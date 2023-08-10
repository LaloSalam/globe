<script>
  import Button from "./Button.svelte";

  let narrowNavMenu = "100vw";
  function openMenu() {
    narrowNavMenu = "0";
  }
  function closeMenu() {
    narrowNavMenu = "100vw";
  }

  let joinWindow;
</script>

<button on:click={openMenu}>
  <svg width="27" height="18" viewBox="0 0 27 18" fill="none" xmlns="http://www.w3.org/2000/svg">
    <line x1="14" y1="1" x2="27" y2="0.999999" stroke="var(--secondary-color)" stroke-width="2" />
    <line x1="7" y1="9" x2="27" y2="9" stroke="var(--secondary-color)" stroke-width="2" />
    <line y1="17" x2="27" y2="17" stroke="var(--secondary-color)" stroke-width="2" />
  </svg>
</button>
<div class="menu" bind:this={narrowNavMenu} style="left: {narrowNavMenu};">
  <div class="head">
    <h1 class="logo"><a href="/">Globe</a></h1>
    <button on:click={closeMenu}>
      <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
        <line x1="18.6655" y1="18.6656" x2="0.807648" y2="0.807741" stroke="#0B0E14" stroke-width="2" />
        <line x1="18.6655" y1="1.33455" x2="0.807619" y2="19.1924" stroke="#0B0E14" stroke-width="2" />
      </svg>
    </button>
  </div>
  <div class="list">
    <nav>
      <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/our-initiatives">Our Initiatives</a></li>
        <li><a href="/about-us">About Us</a></li>
      </ul>
    </nav>
    <Button
      text="Join Our Mission"
      onClick={() => {
        joinWindow = true;
      }}
      fontSize={24}
      backgroundColor="secondary"
      textColor="primary"
    />
  </div>
</div>
<div class="join_window" style="display: {joinWindow ? 'flex' : 'none'}">
  <div class="join_content">
    <svg
      on:click={() => {
        joinWindow = false;
      }}
      width="20"
      height="20"
      viewBox="0 0 20 20"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
    >
      <line x1="18.6655" y1="18.6656" x2="0.807648" y2="0.807741" stroke="#0B0E14" stroke-width="2" />
      <line x1="18.6655" y1="1.33455" x2="0.807619" y2="19.1924" stroke="#0B0E14" stroke-width="2" />
    </svg>
    <h1>Help Save The Earth</h1>
    <p>We'll keep you informed about all our upcoming activities and projects</p>
    <form action="">
      <input class="email" type="email" placeholder="JohnDoe@email.com" />
      <input class="submit" type="submit" value="Join" />
    </form>
  </div>
</div>

<style>
  button {
    background-color: transparent;
    border: none;
  }

  .logo {
    font-family: var(--oswald);
    font-size: 32px;
  }

  .menu {
    position: fixed;
    top: 0;
    height: 100dvh;
    width: 100vw;
    background-color: var(--primary-color);
    z-index: 998;
    transition: all 0.25s ease;
  }

  .head {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    height: 10%;
    padding: 0 24px;
  }

  .list {
    height: 90%;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    gap: 48px;
  }

  ul {
    list-style-type: none;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 20px;
  }
  ul li {
    color: var(--secondary-color);
    font-family: var(--roboto);
    font-size: 32px;
    font-weight: 400;
    cursor: pointer;
    text-align: center;
    border-bottom: 1px solid var(--secondary-color);
    padding: 8px 0;
    text-align: center;
  }
  .join_window {
    width: 100vw;
    height: 100vh;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(255, 255, 255, 0);
    border-radius: 16px;
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(6.4px);
    -webkit-backdrop-filter: blur(6.4px);
    z-index: 999;
    align-items: center;
    justify-content: center;
    display: none;
  }
  .join_content {
    width: 80vw;
    min-height: 400px;
    background-color: var(--primary-color);
    padding: 32px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 16px;
    position: relative;
  }
  .join_content svg {
    position: absolute;
    top: 24px;
    right: 24px;
    cursor: pointer;
  }
  .join_content h1 {
    font-family: var(--oswald);
    font-size: 32px;
    color: var(--secondary-color);
    font-weight: 400;
    width: 100%;
    text-align: center;
  }
  .join_content p {
    font-family: var(--roboto);
    color: var(--secondary-color);
    text-align: center;
  }
  form {
    display: flex;
  }
  .email {
    height: 40px;
    width: 200px;
    border: 1px solid var(--secondary-color);
    font-family: var(--roboto);
    padding-left: 16px;
  }
  .email:focus {
    outline: none;
  }
  .submit {
    height: 40px;
    width: 64px;
    border: none;
    background-color: var(--secondary-color);
    color: var(--primary-color);
    font-family: var(--roboto);
    cursor: pointer;
  }
</style>
