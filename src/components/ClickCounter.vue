<script setup lang="ts">
	import { ref, computed } from 'vue'
	const count = ref<number>(0);
	const countMessage = computed(() => 'Number: ' + count.value);
</script>

<template>
	<div>
		<div>
			{{ countMessage }}
		</div>
		<button @click="count+=998244353">Click!</button>
		<button @click="count = 0">Reset!</button>
	</div>
</template>

<style>
</style>
