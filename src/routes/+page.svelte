<script>
    import { goto } from '$app/navigation';
    
    let newItem = '';
    let todoList = [];


    if (typeof localStorage !== 'undefined') {
        todoList = JSON.parse(localStorage.getItem('todoList')) || [];
    }
    function saveList() {
        localStorage.setItem('todoList', JSON.stringify(todoList));
    }
    function addToList() {
            if (newItem.trim() === '') return;
            todoList = [...todoList, { text: newItem, status: false }];
            newItem = '';
            saveList();
        
    }

    function removeFromList(index) {
        todoList.splice(index, 1);
        todoList = todoList;
        saveList();
    }

    function createPage(url) {
        goto(`/page/${encodeURIComponent(url)}`);
    }
</script>

<br>
<input bind:value={newItem} type="text" placeholder="New todo item...">
<button on:click={addToList}>Add</button>
<br>

{#each todoList as item, index}
    <input bind:checked={item.status} type="checkbox">
    <a on:click={() => createPage(item.text)} class:checked={item.status}>{item.text}</a>
    <span on:click={() => removeFromList(index)}>❌</span>
    <br/>
{/each} 

<style>
    .checked {
        text-decoration: line-through;
        color: gray;
    }
    a:hover, .checked, span {
    cursor: pointer;
}

    a:hover {
       color: blue;
    }

 </style>

