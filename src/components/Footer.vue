<script setup>
import projectData from '../data/projects.json'
</script>

<template>
    <footer class="p-4 p-md-4">
        <div class="row d-flex justify-content-end gap-4 text-white px-md-5">
            <div class="col-md-4 col-lg-3">
                <h5 class="mb-3">Projects</h5>
                <div class="footer-content d-flex flex-column gap-2">
                    <p v-for="project in projectData" :key="project.title">{{ project.title }}</p>
                </div>
            </div>
            <div class="col-md-3">
                <h5 class="mb-3">Contact</h5>
                <div class="footer-content d-flex flex-column gap-1">
                    <p>Manila, Philippines</p>
                    <p>giannasemail@gmail.com</p>
                    <p>09123456789</p>
                </div>
            </div>
        </div>
        <div class="pt-5">
            <span id="copyright" class="text-white fs-6 ms-md-3">© 2026 Copyright: Gianna's Developer Portfolio</span>
        </div>
    </footer>
</template>