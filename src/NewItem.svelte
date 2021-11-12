<script>
    import {createEventDispatcher} from "svelte";

    let item = '';

    const dispatcher = createEventDispatcher();

    function handleClick(e) {
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

    @media (min-width: 640px) {
        main {
            max-width: none;
        }
    }
</style>