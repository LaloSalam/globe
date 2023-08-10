<script>
  import Button from "./Button.svelte";
  import { gsap } from "gsap/dist/gsap";
  import { ScrollTrigger } from "gsap/dist/ScrollTrigger";
  import { onMount } from "svelte";

  gsap.registerPlugin(ScrollTrigger);

  onMount(() => {
    gsap.to(".join_us_section", {
      scrollTrigger: {
        trigger: ".join_us_section",
        scrub: true,
        start: "top 700vh",
        end: "bottom 730vh",
      },
      opacity: 1,
    });
  });

  let joinWindow;
</script>

<section class="join_us_section">
  <div class="header">
    <h2>Get Involved</h2>
    <h1>Be A Part Of The Change</h1>
  </div>
  <div class="bottom">
    <div class="right">
      <p>
        At Globe Climate Action, we believe that every individual has the power to make a difference in the fight against climate change. By getting involved with our community, you're joining a global movement dedicated to preserving our planet for
        future generations.
      </p>
      <Button
        text="Join Our Mission"
        onClick={() => {
          joinWindow = true;
        }}
        fontSize="16"
        backgroundColor="secondary"
        textColor="primary"
      />
    </div>
    <div class="left">
      <img src="Group 5.svg" alt="" />
    </div>
  </div>
</section>

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
  section {
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 32px;
    opacity: 0;
    transition: all 0.2s ease;
    padding: 32px;
    margin-bottom: 32px;
  }
  .header {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }
  h2 {
    font-family: var(--oswald);
    font-weight: 400;
    font-size: 24px;
    color: var(--secondary-color);
  }
  h1 {
    font-family: var(--oswald);
    font-weight: 500;
    font-size: 32px;
    color: var(--secondary-color);
  }
  .bottom {
    display: flex;
    flex-direction: column-reverse;
    width: 100%;
    justify-content: center;
    gap: 32px;
  }
  .right {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 100%;
    gap: 24px;
  }
  p {
    font-family: var(--roboto);
    color: var(--secondary-color);
    opacity: 0.8;
    font-size: 16px;
  }
  .left {
    width: 100%;
    display: flex;
    justify-content: center;
  }
  img {
    width: 40%;
    height: auto;
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
