<script>
  import FullWideHeader from "../../Components/FullWideHeader.svelte";
  import FullNarrowHeader from "../../Components/FullNarrowHeader.svelte";
  import Footer from "../../Components/Footer.svelte";
  import { gsap } from "gsap/dist/gsap";
  import { ScrollTrigger } from "gsap/dist/ScrollTrigger";
  import { onMount } from "svelte";

  let cardStates = {};

  function handleClick(cardId) {
    cardStates[cardId] = !cardStates[cardId];
    cardStates = { ...cardStates };
  }

  let cardData = [
    {
      title: "Green Cities Project",
      content:
        "Our vision is to transform urban landscapes into thriving, eco-friendly communities. Through partnerships with urban planners and local governments, we advocate for sustainable transportation, green spaces, and renewable energy integration. By fostering healthier, resilient cities, we're paving the way for a greener future.",
      img: "green-cities.jpg",
    },
    {
      title: "Ocean Guardianship",
      content:
        "Our oceans are the heart of our planet, and we're on a mission to protect them. Our Ocean Guardianship initiative focuses on ocean conservation, plastic reduction, and marine life preservation. We organize beach clean-ups, collaborate with marine research organizations, and work to raise awareness about the critical role oceans play in maintaining global balance.",
      img: "ocean.jpg",
    },
    {
      title: "Youth Empowerment",
      content:
        "The youth are the driving force behind change. Our Youth Empowerment program provides young individuals with educational workshops, internships, and platforms to express their concerns about climate change. By nurturing the next generation of environmental leaders, we're sowing the seeds for a more sustainable future.",
      img: "youth.jpg",
    },
    {
      title: "Climate Innovators Hub",
      content:
        "Innovation is essential to combat climate change effectively. Our Climate Innovators Hub serves as a platform for researchers, entrepreneurs, and inventors to collaborate on groundbreaking solutions. From renewable energy technologies to sustainable agriculture practices, we're fostering innovation that addresses pressing environmental challenges.",
      img: "climate.jpg",
    },
    {
      title: "Advocacy and Policy",
      content:
        "Change happens when voices unite. Through our Advocacy and Policy initiative, we engage with policymakers, organize awareness campaigns, and promote sustainable policies at local and global levels. We believe that policy changes are crucial for achieving meaningful, large-scale impact.",
      img: "advocacy.jpg",
    },
  ];

  gsap.registerPlugin(ScrollTrigger);

  onMount(() => {
    gsap.to(".card", {
      scrollTrigger: {
        trigger: ".content",
        scrub: 1,
        start: "top 700vh",
        end: "bottom 700vh",
      },
      stagger: 1,
      opacity: 1,
      top: 10,
    });
  });

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
  <section class="heading_container">
    <h2>Our Initiatives</h2>
    <h1>Driving Change for a Sustainable World</h1>
    <p>
      At Globe Climate Action, we're committed to tackling the pressing challenges of climate change through a range of impactful initiatives. Each initiative reflects our dedication to creating a sustainable future for our planet and its
      inhabitants.
    </p>
    <svg width="36" height="34" viewBox="0 0 36 34" fill="none" xmlns="http://www.w3.org/2000/svg">
      <g clip-path="url(#clip0_97_43)">
        <path d="M10 17L18 25L26 17" stroke="#212A3A" />
        <path d="M10 25L18 33L26 25" stroke="#212A3A" />
      </g>
      <path
        d="M6.20312 9.125C6.20312 8.85938 6.17188 8.625 6.10938 8.42188C6.04688 8.21354 5.9375 8.02604 5.78125 7.85938C5.625 7.69271 5.40625 7.53385 5.125 7.38281C4.84375 7.23177 4.48698 7.07812 4.05469 6.92188C3.58594 6.75521 3.16146 6.57031 2.78125 6.36719C2.40104 6.15885 2.07552 5.92188 1.80469 5.65625C1.53906 5.39062 1.33333 5.08594 1.1875 4.74219C1.04167 4.39844 0.96875 4.00521 0.96875 3.5625C0.96875 3.11979 1.04427 2.71094 1.19531 2.33594C1.35156 1.96094 1.57031 1.63542 1.85156 1.35938C2.13802 1.07812 2.48177 0.859375 2.88281 0.703125C3.28385 0.546875 3.73177 0.46875 4.22656 0.46875C4.96615 0.46875 5.58854 0.632812 6.09375 0.960938C6.60417 1.28385 6.98958 1.70833 7.25 2.23438C7.51042 2.75521 7.64062 3.3125 7.64062 3.90625H6.20312C6.20312 3.47917 6.13281 3.10156 5.99219 2.77344C5.85677 2.4401 5.64323 2.17969 5.35156 1.99219C5.0651 1.79948 4.6901 1.70312 4.22656 1.70312C3.8099 1.70312 3.46615 1.78385 3.19531 1.94531C2.92969 2.10677 2.73177 2.32552 2.60156 2.60156C2.47656 2.8776 2.41406 3.19271 2.41406 3.54688C2.41406 3.78646 2.45573 4.00521 2.53906 4.20312C2.6224 4.39583 2.75 4.57552 2.92188 4.74219C3.09896 4.90885 3.31771 5.0625 3.57812 5.20312C3.84375 5.34375 4.15625 5.47917 4.51562 5.60938C5.07292 5.79167 5.54948 5.99479 5.94531 6.21875C6.34115 6.44271 6.66406 6.69531 6.91406 6.97656C7.16406 7.2526 7.34635 7.56771 7.46094 7.92188C7.58073 8.27083 7.64062 8.66667 7.64062 9.10938C7.64062 9.57292 7.5625 9.99219 7.40625 10.3672C7.25521 10.7422 7.03385 11.0625 6.74219 11.3281C6.45052 11.5938 6.09896 11.7995 5.6875 11.9453C5.27604 12.0859 4.8125 12.1562 4.29688 12.1562C3.84896 12.1562 3.40885 12.0833 2.97656 11.9375C2.54948 11.7917 2.16146 11.5729 1.8125 11.2812C1.46354 10.9896 1.1849 10.6302 0.976562 10.2031C0.768229 9.77083 0.664062 9.27083 0.664062 8.70312H2.10156C2.10156 9.09375 2.15885 9.42969 2.27344 9.71094C2.38802 9.98698 2.54688 10.2161 2.75 10.3984C2.95312 10.5807 3.1849 10.7161 3.44531 10.8047C3.71094 10.888 3.99479 10.9297 4.29688 10.9297C4.71354 10.9297 5.0625 10.8568 5.34375 10.7109C5.63021 10.5651 5.84375 10.3568 5.98438 10.0859C6.13021 9.8151 6.20312 9.49479 6.20312 9.125ZM12.2656 10.9766C12.5417 10.9766 12.7917 10.9219 13.0156 10.8125C13.2448 10.6979 13.4323 10.5208 13.5781 10.2812C13.724 10.0365 13.8073 9.71875 13.8281 9.32812H15.125C15.1042 9.89062 14.9609 10.3854 14.6953 10.8125C14.4349 11.2344 14.0911 11.5651 13.6641 11.8047C13.2422 12.0391 12.776 12.1562 12.2656 12.1562C11.7188 12.1562 11.2422 12.0677 10.8359 11.8906C10.4349 11.7135 10.1016 11.4583 9.83594 11.125C9.57552 10.7865 9.38021 10.3776 9.25 9.89844C9.11979 9.41406 9.05469 8.86458 9.05469 8.25V7.29688C9.05469 6.68229 9.11979 6.13542 9.25 5.65625C9.38021 5.17188 9.57552 4.76302 9.83594 4.42969C10.1016 4.09115 10.4349 3.83333 10.8359 3.65625C11.2422 3.47917 11.7188 3.39062 12.2656 3.39062C12.8385 3.39062 13.3333 3.51302 13.75 3.75781C14.1719 3.9974 14.5 4.34635 14.7344 4.80469C14.974 5.25781 15.1042 5.80729 15.125 6.45312H13.8281C13.8073 6.03646 13.7318 5.6901 13.6016 5.41406C13.4714 5.13281 13.2943 4.92448 13.0703 4.78906C12.8464 4.64844 12.5781 4.57812 12.2656 4.57812C11.901 4.57812 11.599 4.64323 11.3594 4.77344C11.125 4.89844 10.9401 5.08073 10.8047 5.32031C10.6693 5.5599 10.5729 5.84635 10.5156 6.17969C10.4635 6.51302 10.4375 6.88542 10.4375 7.29688V8.25C10.4375 8.66146 10.4635 9.03646 10.5156 9.375C10.5729 9.70833 10.6667 9.99479 10.7969 10.2344C10.9323 10.474 11.1198 10.6589 11.3594 10.7891C11.599 10.9141 11.901 10.9766 12.2656 10.9766ZM18.1094 4.875V12H16.7266V3.54688H18.0625L18.1094 4.875ZM20.2109 3.5L20.2188 4.84375C20.1042 4.81771 20 4.80208 19.9062 4.79688C19.8177 4.78646 19.7135 4.78125 19.5938 4.78125C19.3333 4.78125 19.1042 4.83333 18.9062 4.9375C18.7135 5.04167 18.5469 5.1875 18.4062 5.375C18.2656 5.5625 18.1536 5.78646 18.0703 6.04688C17.987 6.30208 17.9297 6.58333 17.8984 6.89062L17.5391 7.125C17.5391 6.61458 17.5781 6.13542 17.6562 5.6875C17.7396 5.23958 17.8672 4.84375 18.0391 4.5C18.2109 4.15104 18.4297 3.88021 18.6953 3.6875C18.9661 3.48958 19.2891 3.39062 19.6641 3.39062C19.7474 3.39062 19.849 3.40365 19.9688 3.42969C20.0938 3.45052 20.1745 3.47396 20.2109 3.5ZM21.1562 8.17969V7.375C21.1562 6.71875 21.2396 6.14323 21.4062 5.64844C21.5729 5.14844 21.8047 4.73177 22.1016 4.39844C22.3984 4.0651 22.7448 3.8151 23.1406 3.64844C23.5365 3.47656 23.9609 3.39062 24.4141 3.39062C24.8776 3.39062 25.3073 3.47656 25.7031 3.64844C26.099 3.8151 26.4453 4.0651 26.7422 4.39844C27.0443 4.73177 27.2786 5.14844 27.4453 5.64844C27.612 6.14323 27.6953 6.71875 27.6953 7.375V8.17969C27.6953 8.83594 27.612 9.41406 27.4453 9.91406C27.2786 10.4089 27.0469 10.8229 26.75 11.1562C26.4531 11.4896 26.1068 11.7396 25.7109 11.9062C25.3151 12.0729 24.888 12.1562 24.4297 12.1562C23.9714 12.1562 23.5443 12.0729 23.1484 11.9062C22.7526 11.7396 22.4036 11.4896 22.1016 11.1562C21.8047 10.8229 21.5729 10.4089 21.4062 9.91406C21.2396 9.41406 21.1562 8.83594 21.1562 8.17969ZM22.5391 7.375V8.17969C22.5391 8.64323 22.5859 9.04948 22.6797 9.39844C22.7734 9.7474 22.9062 10.0391 23.0781 10.2734C23.25 10.5078 23.4505 10.6849 23.6797 10.8047C23.9089 10.9193 24.1589 10.9766 24.4297 10.9766C24.7422 10.9766 25.0156 10.9193 25.25 10.8047C25.4896 10.6849 25.6875 10.5078 25.8438 10.2734C26 10.0391 26.1172 9.7474 26.1953 9.39844C26.2734 9.04948 26.3125 8.64323 26.3125 8.17969V7.375C26.3125 6.91146 26.2656 6.50781 26.1719 6.16406C26.0781 5.8151 25.9453 5.52344 25.7734 5.28906C25.6016 5.04948 25.3984 4.8724 25.1641 4.75781C24.9349 4.63802 24.6849 4.57812 24.4141 4.57812C24.1484 4.57812 23.901 4.63802 23.6719 4.75781C23.4427 4.8724 23.2422 5.04948 23.0703 5.28906C22.9036 5.52344 22.7734 5.8151 22.6797 6.16406C22.5859 6.50781 22.5391 6.91146 22.5391 7.375ZM30.9609 0V12H29.5859V0H30.9609ZM34.6328 0V12H33.2578V0H34.6328Z"
        fill="#212A3A"
      />
      <defs>
        <clipPath id="clip0_97_43">
          <rect width="18" height="18" fill="white" transform="translate(9 16)" />
        </clipPath>
      </defs>
    </svg>
  </section>
  <section class="content">
    {#each cardData as card, index}
      <div class="card" key={index}>
        <div class="card_title" on:click={() => handleClick(index)}>
          <p class="card_title_p">{card.title}</p>
        </div>
        <div class="cards_retractable" style="height: {cardStates[index] ? 400 : 0}px; padding: {cardStates[index] ? 24 : 0}px;">
          <p>{card.content}</p>
          <div class="img" style="background-image: url({card.img});" />
        </div>
      </div>
    {/each}
  </section>
</main>
<Footer />

<style>
  main {
    width: 100%;
    padding: 0 96px;
  }
  .heading_container {
    height: 80vh;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }
  h2 {
    text-align: center;
    font-family: var(--oswald);
    font-size: 34px;
    font-weight: 32;
    color: var(--secondary-color);
  }
  h1 {
    text-align: center;
    font-family: var(--oswald);
    font-size: 56px;
    color: var(--secondary-color);
  }
  .heading_container p {
    margin: 24px 0 64px 0;
    text-align: center;
    font-family: var(--roboto);
    color: var(--secondary-color);
    width: 550px;
  }
  svg {
    position: relative;
    animation: bounce 2s infinite;
    transform: scale(10);
    top: 100px;
  }
  @keyframes bounce {
    0%,
    100% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(-10px);
    }
  }
  .content {
    width: 100%;
    margin: 56px 0 180px 0;
    display: flex;
    flex-direction: column;
    gap: 24px;
  }
  .card {
    width: 100%;
    border-bottom: 1px solid var(--secondary-color);
    position: relative;
    opacity: 0;
    transition: all 0.2s ease;
  }
  .card_title {
    cursor: pointer;
  }
  .card_title_p {
    font-size: 80px;
    font-family: var(--oswald);
    font-style: italic;
    font-weight: 300;
    transition: all 0.2s ease;
  }
  .cards_retractable {
    overflow: hidden;
    transition: all 0.2s ease;
    transform-origin: top;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .cards_retractable p {
    width: 30%;
    font-family: var(--roboto);
    font-size: 24px;
    font-weight: 300;
  }
  .cards_retractable .img {
    height: 300px;
    width: 600px;
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
  }

  @media (max-width: 1300px) {
    .cards_retractable p {
      width: 50%;
    }
    .cards_retractable .img {
      width: 400px;
    }
  }

  @media (max-width: 930px) {
    main {
      padding: 0 32px;
    }
    h1 {
      font-size: 48px;
      font-weight: 500;
    }
    .heading_container p {
      width: 100%;
    }
    svg {
      top: 50px;
    }
    .content {
      margin-bottom: 64px;
    }
    .card_title_p {
      font-size: 40px;
    }
    .cards_retractable {
      flex-direction: column-reverse;
      gap: 8px;
      align-items: flex-start;
    }
    .cards_retractable p {
      width: 100%;
      height: 50%;
      font-size: 16px;
    }
    .cards_retractable .img {
      width: 100%;
      height: 50%;
    }
  }
</style>
