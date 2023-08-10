<script>
  import { gsap } from "gsap/dist/gsap";
  import { ScrollTrigger } from "gsap/dist/ScrollTrigger";
  import { onMount } from "svelte";

  gsap.registerPlugin(ScrollTrigger);
  onMount(() => {
    gsap.to(".second_section_char", {
      scrollTrigger: {
        trigger: ".second_section",
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
        start: "top 400vh",
        end: "bottom 350vh",
        scrub: true,
      },
      opacity: 1,
    });
    gsap.to(".second_sub", {
      scrollTrigger: {
        trigger: ".second_sub",
        start: "top 500vh",
        end: "bottom 450vh",
        scrub: true,
      },
      opacity: 1,
    });
  });
</script>

<section class="second_section" style="background-image: url('My project.png');">
  <div class="sub">
    <div class="square" />
    <p>Climate change poses a grave threat to Earth's ecosystems. Rising temperatures lead to melting ice caps, triggering sea level rise and endangering coastal communities.</p>
  </div>
  <h1 class="h1">
    <span class="second_section_char">SAVE</span>
    <span class="second_section_char">THE</span>
    <span class="second_section_char">MOTHER</span>
    <span class="second_section_char home_char">EARTH</span>
  </h1>
  <div class="second_sub">
    <div class="square" />
    <p>Extreme weather events intensify, causing widespread destruction. Biodiversity loss accelerates as habitats shift rapidly. Urgent action is crucial to mitigate these impacts and safeguard our planet's future.</p>
  </div>
</section>

<style>
  .sub {
    display: flex;
    gap: 8px;
    align-items: flex-start;
    position: absolute;
    left: 156px;
    top: 250px;
    opacity: 0;
  }
  .second_sub {
    display: flex;
    gap: 8px;
    align-items: flex-start;
    position: absolute;
    right: 156px !important;
    bottom: 250px !important;
    opacity: 0;
  }
  .square {
    height: 12px;
    width: 12px;
    background-color: var(--secondary-color);
    position: relative;
    top: 4px;
  }
  p {
    color: var(--secondary-color);
    font-family: var(--roboto);
    font-size: 16px;
    width: 250px;
    font-weight: 400;
  }
  section {
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background-position: center;
    background-repeat: no-repeat;
    position: relative;
  }
  h1 {
    font-weight: bold;
    font-family: var(--oswald);
    font-size: 156px;
    line-height: 105%;
    text-align: center;
    color: var(--secondary-color);
    display: flex;
    flex-direction: column;
  }
  .second_section_char {
    opacity: 0;
  }
  .home_char {
    color: #49adfa;
  }

  @media (max-width: 1400px) {
    .sub {
      left: 64px;
    }
    .second_sub {
      right: 32px !important;
    }
  }
  @media (max-width: 1110px) {
    .second_sub {
      top: 250px !important;
      bottom: unset !important;
      right: 32px !important;
    }
  }
</style>
