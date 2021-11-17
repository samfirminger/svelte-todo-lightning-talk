<script>
    // Imports
    import {setContext} from 'svelte';
    import NewItem from "./NewItem.svelte";
    import Items from "./Items.svelte";
    import Stats from "./Stats.svelte";

    // Set up variables
    let items = [];
    $: doneCount = items.filter(item => item.done).length;

    // Component functions
    function addToItems(e) {
        items = [...items, e.detail];
    }

    function deleteItem(index) {
        items.splice(index, 1);
        items = items;
    }

    function tickItem(index) {
        if (!items[index].done) {
            items[index].done = true;
            items = items;
        }
    }

    // Set context map
    setContext("deleteItem", deleteItem);
    setContext("tickItem", tickItem);

</script>

<!--{@debug items}-->

<main>
    <h1>Sam's ⚡💬 To-do List</h1>
    <div class="todo">
        <NewItem on:addNewItem={addToItems}/>
        <Stats items={items} doneCount={doneCount}/>
        <Items items={items} on:deleteItem={deleteItem} on:tickItem={tickItem}/>
    </div>
</main>


<style>
    main {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        padding: 1em;
        margin: 0 auto;
    }

    h1 {
        color: #ff3e00;
        text-transform: uppercase;
        font-size: 4em;
        font-weight: 100;
    }

    @media (min-width: 640px) {
        main {
            max-width: none;
        }
    }

    .todo {
        width: 500px;
    }
</style>