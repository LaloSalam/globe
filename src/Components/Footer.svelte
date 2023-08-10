<footer>
  <h1><a href="/">Globe</a></h1>
  <ul class="nav">
    <li><a href="/">Home</a></li>
    <li><a href="/our-initiatives">Our Initiatives</a></li>
    <li><a href="/about-us">About Us</a></li>
  </ul>
  <p>© 2023 Globe Climate Action. All rights reserved.</p>
</footer>

<style>
  footer {
    width: 100%;
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: 1fr 1fr 30px;
    row-gap: 16px;
    background-color: var(--secondary-color);
    color: var(--primary-color);
    font-family: var(--oswald);
    padding: 24px 96px;
  }
  h1 {
    grid-column: 1/2;
    grid-row: 1/3;
    font-weight: 400;
  }
  .nav {
    grid-column: 2/3;
    grid-row: 1/3;
    display: flex;
    list-style-type: none;
    align-items: center;
    justify-content: flex-end;
    gap: 16px;
    font-weight: 300;
    font-family: var(--roboto);
  }
  .nav li a {
    text-decoration: none;
    color: var(--primary-color);
  }
  p {
    grid-column: 1/3;
    grid-row: 3/4;
    text-align: center;
    border-top: 0.5px solid var(--primary-color);
    opacity: 0.7;
    padding: 8px 0;
    font-weight: 300;
    font-family: var(--roboto);
  }

  @media (max-width: 850px) {
    footer {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      padding: 24px 32px;
    }
    .nav {
      flex-direction: column;
      align-items: flex-start;
    }
  }
</style>
