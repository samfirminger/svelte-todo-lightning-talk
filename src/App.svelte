<script>
    import {setContext} from 'svelte';
    import NewItem from "./NewItem.svelte";
    import Items from "./Items.svelte";

    let items = [];

    function addToItems(e) {
        items = [...items, e.detail];
    }

    function deleteItem(index) {
        items.splice(index, 1);
        items = items;
    }

    function tickItem(index) {
        items[index].done = true;
        items = items;
    }

    setContext("deleteItem", deleteItem);
    setContext("tickItem", tickItem);


</script>

<!--{@debug items}-->

<main>
    <h1>Triptease To-do List</h1>
    <NewItem on:addNewItem={addToItems}/>
    <Items items={items} on:deleteItem={deleteItem} on:tickItem={tickItem}/>
</main>


<style>
    main {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        padding: 1em;
        max-width: 240px;
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
</style>