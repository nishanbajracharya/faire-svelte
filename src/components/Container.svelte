<style>
  @media (min-width: 65em) {
    .container {
      padding: 0;
    }
  }

  @media (min-width: 64em) {
    .container {
      margin: 0 auto;
      max-width: 64em;
    }
  }

  .container {
    padding: 0 20px;
  }
</style>

<div class="container">
  <slot />
</div>
