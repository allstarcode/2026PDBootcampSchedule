<script lang="ts">
  type link = {
    displayText: string;
    linkURL: string;
  };
  export let actname: string;
  export let links: link[];
  export let classes: string;
</script>

<li class={classes ? 'collection-item ' + classes : 'collection-item'}>
  <h5>{actname}</h5>
  {#each links as link}
    <a class="gen-link" target="_blank" href={link.linkURL}
      >{link.displayText}</a
    >
  {/each}
</li>
