<script>
  /**
   * Specify the file name status
   * @type {"uploading" | "edit" | "complete"}
   */
  export let status = "uploading";

  /** Specify the ARIA label used for the status icons */
  export let iconDescription = "";

  /** Set to `true` to indicate an invalid state */
  export let invalid = false;

  import Close16 from "../icons/Close16.svelte";
  import CheckmarkFilled16 from "../icons/CheckmarkFilled16.svelte";
  import WarningFilled16 from "../icons/WarningFilled16.svelte";
  import Loading from "../Loading/Loading.svelte";
</script>

{#if status === "uploading"}
  <Loading
    description="{iconDescription}"
    {...$$restProps}
    small
    withOverlay="{false}"
  />
{/if}

{#if status === "edit"}
  {#if invalid}
    <WarningFilled16 class="bx--file-invalid" />
  {/if}
  <Close16
    aria-label="{iconDescription}"
    title="{iconDescription}"
    class="bx--file-close"
    {...$$restProps}
    on:click
    on:keydown
  />
{/if}

{#if status === "complete"}
  <CheckmarkFilled16
    aria-label="{iconDescription}"
    title="{iconDescription}"
    class="bx--file-complete"
    {...$$restProps}
  />
{/if}
