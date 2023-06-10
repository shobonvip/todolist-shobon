<script setup lang = "ts">

import { ref } from 'vue';

interface TodoItem{
	name: string
};

const todoItemList = ref<TodoItem[]>([
	{name: 'nanka'}
]);

const finishedItemList = ref<TodoItem[]>([
	{name: '998'}
]);

const newItemName = ref<string>('');

const addNewItem = () => {
	if (newItemName.value === ''){
		return;
	}

	todoItemList.value.push(
		{name: newItemName.value}
	);

	newItemName.value = '';
};

const finishItem = (targetItem: TodoItem) => {
	console.log(targetItem.name);
	todoItemList.value.splice(
		todoItemList.value.indexOf(targetItem), 1
	);
	finishedItemList.value.push(targetItem);
}

</script> 

<template>
	<div>
		<div>
			Todo List
		</div>

		<div>
			mada
			<ul>
				<li
					v-for = "item in todoItemList"
					:key = "item.name"
				>
					<div>
						Name : {{ item.name }}
					</div>

					<button @click = "finishItem(item);">
						Finish!
					</button>

				</li>
			</ul>
		</div>

		<div>
			<label>
				Name
				<input v-model = "newItemName" type = "text" />
			</label>
			<button @click = "addNewItem">
				Add
			</button>
		</div>

		
		<div>
			finished
			<ul>
				<li
					v-for = "item in finishedItemList"
					:key = "item.name"
				>
					<div>
						Name : {{ item.name }}
					</div>
				</li>
			</ul>
		</div>

	</div>
</template>

<style>

</style>