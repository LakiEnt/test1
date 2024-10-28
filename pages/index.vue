<template>
	
	<section class="container">
		<div class="flex space-x-5">
			<select v-model="currentLang" class="">
		    	<option selected>Выберите язык</option>
		    	<option v-for="{code, label} in languagesSelect" :value="code">
		    		{{label}}
		    	</option>
		  	</select>
		</div>


		<div class="flex flex-col space-y-5 transition duration-300">
			<article 
				class="bg-grey-100 max-w-xs p-2 group relative transition duration-300"
				v-for="card in data"
			>
				<h3 class="">
					{{card.locale.ru.cg_name}}
				</h3>

				<div class="rounded-2xl absolute group-hover:relative z-10">
					<NuxtLink 
						class="ml-4 group-hover:opacity-100 opacity-0  -translate-x-full group-hover: translate-x-0 duration-300 block" 
						v-for="child in card.childs"
						:to="child.locale.ru.link"
					>
						- {{child.locale.ru.cg_name}}
					</NuxtLink>
					<p>Fine print: {{}}</p>
				</div>
			</article>
	   </div>
	   
	   <!-- <TreeNode :node="data[0]"/> -->

	</section>
</template>

<script setup lang="ts">
import TreeNode from '~/components/tree-node/TreeNode.vue'
const data = ref()

fetch('task_json.txt')
	.then(val => val.json())
	.then(val => data.value = val)

const currentLang = ref('')
const languagesSelect:[] = [
	{
		code: 'en',
		label:'Английский',
	},
	{
		code: 'ru',
		label:'Русский',
	},
	{
		code: 'fr',
		label:'Францзуский',
	},
] 
</script>
