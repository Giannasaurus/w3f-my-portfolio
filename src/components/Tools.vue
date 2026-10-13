<script setup>
const tools = [
    'html5/html5-original.svg',
    'css3/css3-original.svg',
    'javascript/javascript-original.svg',
    'markdown/markdown-original.svg',
    'latex/latex-original.svg',
    'mongodb/mongodb-original.svg',
    'figma/figma-original.svg',
    'electron/electron-original.svg',
    'bootstrap/bootstrap-original.svg',
    'nodejs/nodejs-original-wordmark.svg',
    'express/express-original.svg',
    'vitejs/vitejs-original.svg',
    'vscode/vscode-original.svg',
    'git/git-original.svg',
    'github/github-original.svg',
    'amazonwebservices/amazonwebservices-original-wordmark.svg',
    'trello/trello-original.svg',
]
</script>

<template>
    <section id="tools" class="d-flex flex-column align-items-start mx-4 mx-md-5 mb-5">
        <h2 class="lh-1 mb-5 mb-lg-4">My Tools</h2>
        <div class="d-flex justify-content-center align-items-center">
            <div id="tools-container"
                class="d-flex flex-wrap justify-content-center align-items-center px-md-5 gap-md-3">
                <img v-for="tool in tools" :key="tool"
                    :src="`https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/${tool}`"
                    :alt="tool.split('/')[0]">
            </div>
        </div>
    </section>
</template>