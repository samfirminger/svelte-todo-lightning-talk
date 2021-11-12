<script>
    // Imports
    import Item from "./Item.svelte";

    // Props from parent
    export let items;
</script>

<div class="todo-container">
    {#each items as item, index}
        <Item item={item} index={index} on:click/>
    {/each}
</div>


<style>
    .todo-container {
        margin-top: 30px;
    }
</style>