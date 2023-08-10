<script>
  import FullWideHeader from "../../Components/FullWideHeader.svelte";
  import FullNarrowHeader from "../../Components/FullNarrowHeader.svelte";
  import Footer from "../../Components/Footer.svelte";

  let screenWidth;
</script>

<svelte:window bind:innerWidth={screenWidth} />

{#if screenWidth <= 930}
  <FullNarrowHeader />
{/if}
{#if screenWidth > 930}
  <FullWideHeader />
{/if}
<main>
  <section class="first_section">
    <h1>About Us <br /> <span>Driving Positive Change <br /> for a Sustainable Future</span></h1>
    <p>
      At Globe Climate Action, we're on a mission to address the critical challenges posed by climate change and promote environmental sustainability on a global scale. Our organization was founded with the belief that collective action, innovation,
      and education are key to creating a better world for ourselves and future generations.
    </p>
  </section>
  <div class="first_section_img" style="background-image: url('waterfall.jpg');" />
  <section class="second_section">
    <div class="line">
      <h1>Our Vision</h1>
      <p>Our vision is a world where the delicate balance of ecosystems is preserved, where communities thrive in harmony with nature, and where all individuals understand and actively contribute to a sustainable future.</p>
    </div>
    <div class="line">
      <h1>Our Mission</h1>
      <p>
        Globe Climate Action's mission is to drive positive change through a range of initiatives that tackle climate change from various angles. We combine advocacy, education, hands-on projects, and partnerships to make a meaningful impact on both
        local communities and the broader global landscape.
      </p>
    </div>
  </section>
</main>
<Footer />

<style>
  .first_section {
    width: 100%;
    height: 40vh;
    padding: 64px 96px;
    display: flex;
    align-items: flex-end;
    justify-content: center;
    gap: 10%;
  }
  .first_section h1 {
    font-family: var(--oswald);
    font-weight: 400;
    font-size: 56px;
    line-height: 101%;
    color: var(--secondary-color);
  }
  .first_section h1 span {
    font-weight: 300;
  }
  .first_section p {
    width: 500px;
    font-family: var(--roboto);
    font-weight: 300;
    color: var(--secondary-color);
  }
  .first_section_img {
    width: 100%;
    height: 50vh;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
  }
  .second_section {
    width: 100%;
    padding: 64px 96px;
    display: flex;
    gap: 48px;
  }
  .line {
    display: flex;
    flex-direction: column;
    gap: 16px;
    margin-bottom: 32px;
    width: 50%;
  }
  .line h1 {
    color: var(--secondary-color);
    font-family: var(--oswald);
    font-size: 32px;
    font-weight: 400;
  }
  .line p {
    color: var(--secondary-color);
    font-family: var(--roboto);
    font-weight: 300;
    font-size: 20px;
  }
  @media (max-width: 930px) {
    .first_section h1 {
      font-size: 40px;
      width: 100%;
    }
    .first_section p {
      width: 100%;
    }
    .first_section {
      padding: 48px 32px;
      flex-direction: column;
    }
    .second_section {
      padding: 48px 32px;
      display: block;
    }
    .line {
      width: unset;
    }
    .line p {
      font-size: 16px;
    }
  }
</style>
