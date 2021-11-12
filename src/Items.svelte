<script>
    import Item from "./Item.svelte";
    export let items;
</script>

<div class="todo-container">
    {#each items as item, index}
        <Item item={item} index={index} on:click/>
    {/each}
</div>


<style>
    .todo-container {
        width: 500px;
        margin-top: 50px;
    }
</style>