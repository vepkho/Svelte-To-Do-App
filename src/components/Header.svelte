<script>
    import {items} from '../store'

    $: itemsCount = $items.length;
    $: completedItemsCount = $items.filter(item => item.completed).length;
</script>
<style>
    .header{
        display: flex;
        align-items: center;
        justify-content: space-between;
        color: #ffffff;
        font-weight: bold;
        font-size: 24px;
        background: rgba(0, 0, 0, 0.1);
        padding: 16px 40px;
    }
</style>

<div class="header">
    <span>Kookla - To-Do List</span>
    <span>
        {completedItemsCount} / {itemsCount}
    </span>
</div>