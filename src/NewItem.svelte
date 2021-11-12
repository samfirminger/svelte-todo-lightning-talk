<script>
    // Imports
    import {createEventDispatcher} from "svelte";

    // Create component variable
    let item = '';
    $: itemHasContent = item.length > 0;

    // Create dispatcher to talk to parent
    const dispatcher = createEventDispatcher();

    function handleClick() {
        if (itemHasContent) {
            dispatcher("addNewItem", {item, done: false});
            item = '';
        }
    }
</script>

<div class="new-item">
    <input type="text" bind:value={item}/>
    <button disabled="{!itemHasContent}" on:click={handleClick}>Add</button>
</div>

<style>
    .new-item {
        display: flex;
        justify-content: space-between;
    }

    input {
        height: 30px;
        width: 400px;
    }

    button {
        height: 30px;
        width: 80px;
        border-radius: 4px;
        cursor: auto;
    }

    .clickable {
        cursor: pointer;
    }

    .clickable:hover {
        background-color: #e9e6e6;
    }

</style>