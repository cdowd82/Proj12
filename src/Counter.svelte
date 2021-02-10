<script>
    export let i
    export let showWorkupList = false;
    let count;
</script>

<div>
    {#if showWorkupList}
        {count = i}
    {/if}
</div>

<style></style>