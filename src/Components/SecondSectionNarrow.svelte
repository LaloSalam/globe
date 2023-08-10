<script>
  import { gsap } from "gsap/dist/gsap";
  import { ScrollTrigger } from "gsap/dist/ScrollTrigger";
  import { onMount } from "svelte";

  gsap.registerPlugin(ScrollTrigger);
  onMount(() => {
    gsap.to(".second_section_char", {
      scrollTrigger: {
        trigger: ".h1",
        start: "top 400vh",
        end: "bottom 730vh",
        scrub: 1,
      },
      opacity: 1,
      duration: 0.2,
      stagger: 0.1,
    });
    gsap.to(".sub", {
      scrollTrigger: {
        trigger: ".sub",
        start: "top 750vh",
        end: "bottom 700dvh",
        scrub: true,
      },
      opacity: 1,
    });
  });
</script>

<section class="second_section" style="background-image: url('My project.png');">
  <h1 class="h1">
    <span class="second_section_char">SAVE</span>
    <span class="second_section_char">THE</span>
    <span class="second_section_char">MOTHER</span>
    <span class="second_section_char home_char">EARTH</span>
  </h1>

  <p class="sub">
    Climate change poses a grave threat to Earth's ecosystems. Rising temperatures lead to melting ice caps, triggering sea level rise and endangering coastal communities. Extreme weather events intensify, causing widespread destruction. Biodiversity
    loss accelerates as habitats shift rapidly. Urgent action is crucial to mitigate these impacts and safeguard our planet's future.
  </p>
</section>

<style>
  section {
    height: 100vh;
    display: flex;
    flex-direction: column;
    gap: 48px;
    align-items: center;
    justify-content: center;
    background-position: center;
    background-repeat: no-repeat;
    background-size: contain;
    position: relative;
  }
  h1 {
    font-weight: bold;
    font-family: var(--oswald);
    font-size: 96px;
    width: 100%;
    line-height: 105%;
    text-align: center;
    display: flex;
    flex-direction: column;
    color: var(--secondary-color);
  }
  .second_section_char {
    opacity: 0;
  }
  .home_char {
    color: #49adfa;
  }
  p {
    color: var(--secondary-color);
    font-family: var(--roboto);
    font-size: 16px;
    width: 100%;
    font-weight: 400;
    opacity: 0;
    padding: 24px;
  }
</style>
