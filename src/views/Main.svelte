<script>
import Container from '../components/Container.svelte';
</script>

<style>
  .appbar {
    top: 0;
    z-index: 1;
    width: 100%;
    position: fixed;
    background: #fff;
    box-shadow: 0 1px 2px rgba(0, 0, 0, 0.25);
  }

  :global(.appbar .container) {
    height: 64px;
    display: flex;
    padding: 0 20px;
    align-items: center;
    justify-content: space-between;
  }

  .main-container {
    margin-top: 64px;
  }

  @media (min-width: 65em) {
    :global(.appbar .container) {
      padding: 0;
    }
  }
</style>

<div class="appbar"><Container>hello</Container></div>
<div class="main-container">
  <Container><slot /></Container>
</div>
