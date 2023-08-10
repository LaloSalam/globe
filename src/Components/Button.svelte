<script>
  export let text;
  export let fontSize;
  export let fontWeight;
  export let backgroundColor;
  export let textColor;
  export let onClick;
</script>

<button on:click={onClick} style="font-size:{fontSize}px; font-weight:{fontWeight}; background-color: var(--{backgroundColor}-color; color: var(--{textColor}-color;">
  {text}
</button>

<style>
  button {
    background-color: var(--secondary-color);
    color: var(--primary-color);
    font-family: var(--roboto);
    font-weight: 500;
    padding: 8px 24px;
    border: none;
    cursor: pointer;
    transition: all 0.5s ease;
    clip-path: inset(0 0 0 0);
  }
</style>
