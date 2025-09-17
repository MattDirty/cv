<script lang="ts">
    export let list: string[] = ["Item 1", "Item 2", "Item 3"];
</script>

<ul class="simple-list">
    {#each list as item}
        <li>{item}</li>
    {/each}
</ul>