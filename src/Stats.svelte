<script>
    // Props from parent
    export let items;
    export let doneCount;

    $: allDone = items.length === doneCount;
    $: statement = allDone ? 'You\'re unstoppable!!!!' : 'I\'m not angry I\'m just disappointed..';

    function getReward() {
        window.location.replace("http://localhost:3400");
    }
</script>

{#if items.length > 0}
    <div>
        <div class="stats">
            <div class="stat"><b>To-do:</b> {items.length}</div>
            <div class="stat"><b>Done:</b> {doneCount}</div>
        </div>
        <div class="status">
            <div>
                <b>Completion Status: </b>
                {statement}
            </div>
            {#if allDone}
                <button on:click={getReward}>Reward</button>
            {/if}
        </div>

    </div>
{/if}

<style>
    .stats {
        display: flex;
        flex-direction: row;
        margin-top: 20px;
    }

    .stat {
        margin-right: 20px;
    }

    .status {
        height: 35px;
        margin-top: 20px;
        display: flex;
        justify-content: space-between;
    }

    button {
        cursor: pointer;
        border-radius: 4px;
        margin: 0;
    }

    button:hover {
        background-color: #e9e6e6;
    }
</style>