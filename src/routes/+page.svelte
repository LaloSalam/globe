<script>
  import HeroSection from "../Components/HeroSection.svelte";
  import SecondSection from "../Components/SecondSection.svelte";
  import HeroSectionNarrow from "../Components/HeroSectionNarrow.svelte";
  import SecondSectionNarrow from "../Components/SecondSectionNarrow.svelte";
  import JoinUsSection from "../Components/JoinUsSection.svelte";
  import JoinUsSectionNarrow from "../Components/JoinUsSectionNarrow.svelte";
  import Footer from "../Components/Footer.svelte";
  import { onMount } from "svelte";

  let screenWidth;

  onMount(() => {
    console.log(screenWidth);
  });
</script>

<svelte:window bind:innerWidth={screenWidth} />

{#if screenWidth <= 930}
  <HeroSectionNarrow />
  <SecondSectionNarrow />
  <JoinUsSectionNarrow />
{/if}
{#if screenWidth > 930}
  <HeroSection />
  <SecondSection />
  <JoinUsSection />
{/if}
<Footer />
<body />
