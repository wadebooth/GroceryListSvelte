<script>
    let newGroceryItem = '';
	
    let groceryList = [{text: 'Fairlife Milk', status: true},
                    {text: 'Air Fryer Chicken', status: false},
                    {text: 'Yogurt', status: false}];
	
	function addToList() {
		groceryList = [...groceryList, {text: newGroceryItem, status: false}];
		newGroceryItem = '';
	}
	
	function removeFromList(index) {
		groceryList.splice(index, 1)
		groceryList = groceryList;
    }
</script>


<input bind:value={newGroceryItem} type="text" placeholder="new grocery item..">
<button on:click={addToList}>Add</button>

<br/>
{#each groceryList as item, index}
	<input bind:checked={item.status} type="checkbox">
	<span class:checked={item.status}>{item.text}</span>
	<span on:click={() => removeFromList(index)}>❌</span>
	<br/>
{/each} 


<style> 
	.checked {
        text-decoration: line-through;
    }
</style> 