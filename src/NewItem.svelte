<script>
    // Imports
    import {createEventDispatcher} from "svelte";

    // Create component variable
    let item = '';

    // Create dispatcher to talk to parent
    const dispatcher = createEventDispatcher();

    function handleClick() {
        dispatcher("addNewItem", {item, done: false});
        item = '';
    }
</script>

<div class="new-item">
    <input type="text" bind:value={item}/>
    <button on:click={handleClick}>Add</button>
</div>

<style>
    .new-item {
        display: flex;
        justify-content: space-between;
        width: 500px;
    }

    input {
        height: 30px;
        width: 400px;
    }

    button {
        height: 30px;
        width: 80px;
        cursor: pointer;
        border-radius: 4px;
    }
</style>