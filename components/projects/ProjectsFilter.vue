<script>
export default {
	props: {
		select: {
			type: String,
			default: 'projects',
			required: true,
		},
		selectOptions: {
			type: Array,
			default: () => [
				'Application development',
				'UI-UX design',
                'Design',
				'Book design',
				'Animation',
			],
		},
		showSelect: {
			type: Boolean,
			default: true,
		},
	},
};
</script>

<template>
	<div v-if="showSelect">
	<select
		@change="$emit('filter', $event.target.value)"
		:name="select"
		:id="select"
		class="font-general-medium
				px-4
				py-2
				border-1 border-gray-200
				dark:border-secondary-dark
				rounded-lg
				text-sm
				sm:text-md
				bg-secondary-light
				dark:bg-ternary-dark
				text-primary-dark
				dark:text-ternary-light
			"
	>
		<option v-if="showAllProjectsOption" value class="text-sm sm:text-md">All Projects</option>
		<option
			v-for="option in selectOptions"
			:key="option"
			:value="option"
			class="sm:text-md"
		>
			{{ option }}
		</option>
	</select>
</div>
</template>
