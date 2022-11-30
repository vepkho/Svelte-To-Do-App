<script>
    import {createEventDispatcher} from "svelte"

    const dispatch = createEventDispatcher();

    let value = "";

    function handleKeyUp({key}) {
        if(key !== "Enter"  || value.length === 0) return;
        dispatch("newitem", value);
        value= "";
    }
</script>

<style>
    input{
        margin-bottom: 16px;
        padding: 16px;
        border: none;
        outline: none;
        width: 100%;
        background-color: rgba(0,0,0, 0.25);
        color: #ffffff;
        font-weight: bold;
        font-size: 16px;
        cursor: pointer;
    }

    input:focus::placeholder{
        color: transparent;
    }

    input::placeholder{
        color: #ffffff;
    }
</style>

<input 
    type="text" 
    on:keyup={handleKeyUp} 
    bind:value
    placeholder="+ Add Item" 
/>