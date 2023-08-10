<script>
  import Button from "../Components/Button.svelte";
  import FullNarrowHeader from "./FullNarrowHeader.svelte";
  import { onMount } from "svelte";
  import { gsap } from "gsap";

  let heroContent = [
    {
      id: 1,
      img: "second.jpg",
      heading: "Penguin Pals Virtual Adoption Drive",
      subheading: "Globe Climate Action presents a unique opportunity to adopt your very own virtual penguin pal!",
      p: 'Globe Climate Action presents a unique opportunity to adopt your very own virtual penguin pal! As climate change affects penguin habitats, our organization has partnered with a renowned virtual reality studio to create an immersive experience. By "adopting" a virtual penguin, you\'ll contribute to our conservation efforts, helping us raise awareness about the impact of melting ice on these adorable creatures. Participants will receive personalized virtual reality videos of their penguin pals, fostering a sense of connection and responsibility toward our icy friends.',
    },
    {
      id: 2,
      img: "third.jpg",
      heading: "Extreme Ice Sculpture Challenge",
      subheading: "Think you've got what it takes to beat climate change at its own game? Join the Extreme Ice Sculpture Challenge brought to you by Globe Climate Action! ",
      p: "Think you've got what it takes to beat climate change at its own game? Join the Extreme Ice Sculpture Challenge brought to you by Globe Climate Action! This exciting event combines art, activism, and adrenaline. Teams will compete to create stunning ice sculptures that convey the effects of climate change while highlighting the urgency of global action. Not only will this challenge showcase the creativity of participants, but it will also raise awareness about the importance of preserving our delicate ecosystems. So grab your chisels and let's sculpt a better future!",
    },
    {
      id: 3,
      img: "first.jpg",
      heading: "Eco-Adventure Clean-Up Expedition",
      subheading: "Join us on an exciting journey to the heart of nature! Globe Climate Action presents the Eco-Adventure Clean-Up Expedition.",
      p: "Join us on an exciting journey to the heart of nature! Globe Climate Action presents the Eco-Adventure Clean-Up Expedition. We're sending out teams of passionate volunteers to remote wilderness areas to clean up plastic debris and waste left behind by previous generations. This not only helps preserve the natural beauty of these untouched landscapes but also raises awareness about the importance of responsible waste disposal. As we hike, climb, and explore, we'll make a positive impact on the environment and leave a cleaner world for future generations.",
    },
  ];

  let index = 0;
  let imgElement;
  let h1Element;
  let pElement;

  $: Cimg = heroContent[index].img;
  $: Cheading = heroContent[index].heading;
  $: Csubheading = heroContent[index].subheading;
  $: Cparagraph = heroContent[index].p;

  let startX;
  let dist = 0;
  const threshold = 100; // Minimum distance for swipe detection (adjust as needed)

  function handleTouchStart(event) {
    startX = event.touches[0].clientX;
    dist = 0;
  }

  function handleTouchMove(event) {
    const currentX = event.touches[0].clientX;
    dist = currentX - startX;
  }

  function handleTouchEnd() {
    if (Math.abs(dist) > threshold) {
      if (dist > 0) {
        console.log("Right swipe detected!");
        handleSwipe();
        setTimeout(() => {
          if (index > 0) {
            index -= 1;
          }
        }, 500);
        clearInterval(interval); // Clear the previous interval
        interval = setInterval(autoChangeIndex, 10000); // Start a new interval
      } else {
        console.log("Left swipe detected!");
        handleSwipe();
        setTimeout(() => {
          if (index < heroContent.length - 1) {
            index += 1;
          }
        }, 500);
        clearInterval(interval); // Clear the previous interval
        interval = setInterval(autoChangeIndex, 10000); // Start a new interval
      }
    }
    dist = 0;
  }

  function handleSwipe() {
    gsap.fromTo(
      ".heading_sub_CTA_container p, .image_container, .heading_sub_CTA_container Button, .heading_sub_CTA_container h1",
      {
        clipPath: "inset(0 100% 0 0)",
        duration: 0.5,
      },
      {
        clipPath: "inset(0 0 0 0)",
        duration: 0.5,
      }
    );
  }

  let interval;

  function contIndexChange(num) {
    handleSwipe();
    setTimeout(() => {
      index = num;
    }, 500);
    clearInterval(interval); // Clear the previous interval
    interval = setInterval(autoChangeIndex, 5000); // Start a new interval
  }

  function autoChangeIndex() {
    handleSwipe();
    setTimeout(() => {
      index = (index + 1) % heroContent.length;
    }, 500);
  }

  onMount(() => {
    interval = setInterval(autoChangeIndex, 5000);

    // Clear the interval when the component is destroyed to avoid memory leaks
    return () => clearInterval(interval);
  });

  function handleSlideChange(id) {
    let iden = id - 1;
    contIndexChange(iden);
  }

  let active;

  let isReading;
  function handleReadMore() {
    clearInterval(interval);
    isReading = true;
  }

  function handleCloseReadMore() {
    interval = setInterval(autoChangeIndex, 5000);
    isReading = false;
  }
</script>

<FullNarrowHeader />
<section class="hero_section" on:touchstart={handleTouchStart} on:touchmove={handleTouchMove} on:touchend={handleTouchEnd}>
  <div class="heading_sub_CTA_container">
    <h1 bind:this={h1Element}>{Cheading}</h1>
    <p bind:this={pElement}>{Csubheading}</p>
    <Button
      text="Read More"
      onClick={() => {
        handleReadMore();
      }}
      fontSize={16}
      backgroundColor="secondary"
      textColor="primary"
    />
  </div>
  <div class="slideshow_buttons_container">
    {#each heroContent as heroContent (heroContent.id)}
      {#if heroContent.id == index + 1}
        <div class="circle active_circle" on:click={() => handleSlideChange(heroContent.id)} />
      {:else}
        <div class="circle" on:click={() => handleSlideChange(heroContent.id)} />
      {/if}
    {/each}
  </div>
  <div bind:this={imgElement} class="image_container" style="background-image: url('{Cimg}');" />
</section>
<div class="read_more" style="display: {isReading ? 'flex' : 'none'}">
  <div class="content">
    <svg on:click={handleCloseReadMore} width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
      <line x1="18.6655" y1="18.6656" x2="0.807648" y2="0.807741" stroke="#0B0E14" stroke-width="2" />
      <line x1="18.6655" y1="1.33455" x2="0.807619" y2="19.1924" stroke="#0B0E14" stroke-width="2" />
    </svg>
    <h1>{Cheading}</h1>
    <p>{Cparagraph}</p>
  </div>
</div>

<style>
  .hero_section {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 90dvh;
    width: 100%;
    padding: 16px 0;
  }
  .heading_sub_CTA_container {
    height: 50%;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: self-start;
    gap: 16px;
    flex-direction: column;
    padding: 0 24px;
  }
  .heading_sub_CTA_container h1 {
    width: 100%;
    font-family: var(--oswald);
    font-size: 40px;
    font-weight: 400;
    color: var(--secondary-color);
    line-height: 104%;
    transition: all 0.5s ease;
    clip-path: inset(0 0 0 0);
    padding: 4px 0;
  }
  .heading_sub_CTA_container p {
    width: 80%;
    padding: 4px 0;
    font-family: var(--roboto);
    font-size: 20px;
    font-weight: 200;
    line-height: 115%;
    color: var(--secondary-color);
    transition: all 0.5s ease;
    clip-path: inset(0 0 0 0);
  }
  .slideshow_buttons_container {
    height: 2.5%;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 8px;
  }
  .circle {
    height: 12px;
    width: 12px;
    border-radius: 50%;
    background-color: var(--secondary-color);
    opacity: 0.4;
    cursor: pointer;
  }
  .active_circle {
    opacity: 1;
  }
  .image_container {
    width: 100%;
    height: 42.5%;
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
    transition: all 0.5s ease;
    clip-path: inset(0 0 0 0);
  }
  .read_more {
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
  .content {
    width: 80vw;
    min-height: 400px;
    background-color: var(--primary-color);
    padding: 32px;
    display: flex;
    flex-direction: column;
    gap: 16px;
    position: relative;
  }
  .content svg {
    position: absolute;
    top: 24px;
    right: 24px;
    cursor: pointer;
  }
  .content h1 {
    font-family: var(--oswald);
    font-weight: 400;
    font-size: 40px;
    color: var(--secondary-color);
  }
  .content p {
    font-family: var(--roboto);
    font-size: 20px;
    font-weight: 300;
    color: var(--secondary-color);
  }
</style>
