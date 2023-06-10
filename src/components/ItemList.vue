<script setup lang="ts">

import { ref } from 'vue'

interface Item{
	name: string,
	price: number
};

const items = ref<Item[]>([
	{name: 'Egg', price: 100},
	{name: 'Apple', price: 160}
]);

const newItemName = ref<string>('');
const newItemPrice = ref<number>(0);

const addItem = () => {
	// If the name is empty, do not add
	if (newItemName.value === ''){
		return;
	}

	items.value.push({
		name: newItemName.value,
		price: newItemPrice.value
	});

	newItemName.value = '';
};

</script>

<template>
	<div>
		<div>ItemList</div>
		<ul>
			<li
				v-for = "item in items"
				:key = "item.name"
				:class = "{over500: item.price >= 500}"
			>
				<div>
					Name: {{ item.name }}
				</div>
				<div>
					{{ item.price }} yen
				</div>
				<div v-if = "item.price >= 998244353">
					実質 {{ item.price % 998244353 }} yen
				</div>
			</li>
		</ul>
		<div>
			<label>
				Name
				<input v-model = "newItemName" type = "text" />
			</label>
			<label>
				Price
				<input v-model = "newItemPrice" type = "number" />
			</label>
			<button @click = "addItem">
				Add
			</button>
		</div>
	</div>
</template>

<style>
.over500 {
	color: red;
}
</style>