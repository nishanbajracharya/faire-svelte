<script>
  export let name = "";
  export let className = "";
</script>

<style>
  i {
    color: #929292;
    font-size: 30px;
    vertical-align: middle;
    transition: 0.2s ease-in-out;
  }

  i.light {
    color: #bababa;
  }

  i.blue {
    color: #49c;
  }
</style>

<i class={`material-icons ${className}`}>{name}</i>
