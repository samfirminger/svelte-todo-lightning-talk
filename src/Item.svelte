<script>
    import {getContext} from "svelte";

    // Props
    export let item;
    export let index;

    // Context
    const deleteItem = getContext("deleteItem");
    const tickItem = getContext("tickItem");

</script>

<div class="todo-item">
    <div class="item" class:checked={item.done}>{item.item}</div>
    <div class="icons">
        <div class="icon-container delete" on:click={deleteItem(index)}>
            <img src="/delete.png" class="item-icon"/>
        </div>
        <div class="icon-container tick" class:tick-checked={item.done} on:click={tickItem(index)}>
            <img src="/tick.png" class="item-icon"/>
        </div>
    </div>
</div>


<style>
    .item {
        width: 70%;
        border-radius: 4px;
    }

    .checked {
        text-decoration: line-through;
    }

    .icons {
        width: 30%;
        display: flex;
        flex-direction: row;
        justify-content: right;
    }

    .icon-container {
        border-radius: 3px;
        cursor: pointer;
        margin-left: 5px;
    }

    .tick-checked {
        background-color: #c4ffc4;
        cursor: auto;
    }

    .delete {
        border: 1px solid #B43D48;
    }

    .tick {
        border: 1px solid #008001;
    }

    .item-icon {
        height: 30px;
        width: 30px;
        padding: 3px;
    }

    .todo-item {
        text-align: left;
        margin-bottom: 20px;
        padding: 10px;
        box-shadow: 0 2px 20px rgba(0, 0, 0, 0.1);
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
</style>