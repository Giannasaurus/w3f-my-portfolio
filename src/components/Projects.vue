<script setup>
import projectData from '../data/projects.json'

const projectImages = import.meta.glob('../../public/images/*.{png,jpg,jpeg,webp,avif}', {
    eager: true,
    import: 'default',
    query: '?url',
})

const projects = projectData.map((project) => ({
    ...project,
    image: projectImages[`../../public/images/${project.image}`],
}))
</script>

<template>
    <section id="projects" class="mx-4 mx-md-5 mb-5">
        <h2 class="lh-1 mb-md-3 mb-5 mb-lg-4">My Projects</h2>
        <div class="row row-cols-1 row-cols-md-2 row-cols-lg-3 g-4">
            <div v-for="project in projects" :key="project.title" class="col d-flex">
                <article class="card">
                    <img :src="project.image" class="card-img-top" :alt="project.title">
                    <div class="card-body p-3">
                        <h5 class="card-title mb-3">{{ project.title }}</h5>
                        <p class="card-text">{{ project.description }}</p>
                    </div>
                </article>
            </div>
        </div>
    </section>
</template>