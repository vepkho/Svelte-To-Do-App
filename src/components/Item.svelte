<script>
    import {createEventDispatcher} from 'svelte'

    export let id, text, completed;

    const dispatch = createEventDispatcher();

    function triggerUpdate() {
        dispatch("update", {id, text, completed});
    }

    function handleDoubleClick() {
        const yes = confirm('Are you sure you wish to delete this item?')

        if (yes) {
            dispatch("delete", id)
        }
    }
</script>

<style>
    .item{
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 8px 16px;
        background-color: #ffffff;
    }

    .item.completed{
        background-color: #ffffff;
    }

    .item.completed .text-input{
        color: #555555;
        text-decoration: line-through;
    }

    .item:focus-within{
        background-color: rgba(255, 255, 255, 0.8);
    }

    .text-input{
        flex-grow: 1;
        background:none;
        border: none;
        outline: none;
        font-weight: 500;
        font-size: 16px;
    }

    .completed-checkbox{
        margin-left: 16px;
        cursor: pointer;
    }
</style>

<div class="item" class:completed on:dblclick={handleDoubleClick}>
    <input 
        class="text-input" 
        type="text" 
        bind:value={text} 
        readonly={completed} 
        on:keyup={({key, target}) => key === "Enter"}  
        on:blur={() => triggerUpdate()}
    />
    <input 
        class="completed-checkbox" 
        type="checkbox" 
        bind:checked={completed} 
        on:change={() => triggerUpdate()}
    />
</div>