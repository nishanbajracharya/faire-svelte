<script>
  import Tab from "../components/Tab.svelte";

  const routes = [
    { label: "Home", to: "/" },
    { label: "Completed", to: "/completed" },
    { label: "Remaining", to: "/remaining" }
  ];
</script>

<style>
  @media (min-width: 64em) {
    :global(.appbar .tab-container) {
      display: flex;
      margin-left: -55px;
    }
  }
  :global(.appbar .nav-container) {
    display: none;
  }
</style>

<div class="tab-container">
  {#each routes as { label, to }, i}
    <Tab {to}>{label}</Tab>
  {/each}
</div>
