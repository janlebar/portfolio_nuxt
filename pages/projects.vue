<script setup>
import ProjectsGrid from '/components/projects/ProjectsGrid.vue';
import Header from '~/components/Header.vue'

const result = await useAsyncData('projects', () => queryContent('projects').find());
const value = result.data.value;

let projects = [];

if (value) {
	projects = value.map((project) => {
		console.log(project.category + 'HERE IN PROJECTS'); // log the category here
		return {
			id: project._id,
			title: project.title,
			// description: project.description,
			img: project.image,	
			maintitle: project.maintitle,
			category: project.category
		}
	});
}
</script>

<template>
    <Header />
	<div class="container mx-auto">
		<ProjectsGrid :allProjects="projects" />
	</div>
</template>
