<script>
  import { Link } from "svelte-routing";

  // Props
  export let to = "#";

  function getProps({ location, href, isPartiallyCurrent, isCurrent }) {
    const isActive = href === "/" ? isCurrent : isPartiallyCurrent || isCurrent;
    // The object returned here is spread on the anchor element's attributes
    if (isActive) {
      return { class: "link active" };
    }
    return { class: "link" };
  }
</script>

<style>
  :global(a) {
    color: #1e87f0;
    text-decoration: none;
    cursor: pointer;
  }

  :global(.appbar .link) {
    width: 170px;
    height: 64px;
    color: #929292;
    align-items: center;
    display: inline-flex;
    box-sizing: border-box;
    justify-content: center;
    border-top: 4px solid transparent;
  }

  :global(.appbar .link.active) {
    color: #49c;
    border-top: 4px solid #49c;
  }

  :global(.appbar .link:hover) {
    text-decoration: none;
    background: rgba(0, 0, 0, 0.04);
  }
</style>

<Link {to} {getProps}>
  <slot />
</Link>
