<script>
  import Button from "./Button.svelte";

  let joinWindow;
</script>

<div>
  <Button
    text="Join Us"
    onClick={() => {
      joinWindow = true;
    }}
    fontSize={16}
    backgroundColor="secondary"
    textColor="primary"
  />
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
  div {
    height: 88px;
    display: flex;
    align-items: center;
    gap: 20px;
    z-index: 999;
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
    font-size: 40px;
    color: var(--secondary-color);
    font-weight: 400;
  }
  .join_content p {
    font-family: var(--roboto);
    color: var(--secondary-color);
  }
  form {
    display: flex;
  }
  .email {
    height: 40px;
    width: 384px;
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
