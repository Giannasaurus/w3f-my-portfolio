<template>
    <section id="contact" class="text-left vh-100 mx-4 mx-md-5 mb-5">
        <h2 class="lh-1 mb-5 mb-lg-4">Contact Me</h2>
        <div class="row g-4">
            <div class="col-12 col-lg-6">
                <p class="ps-2 mb-3 mb-md-5">Please feel free to email me for collaborations on any project!</p>
            </div>
            <form class="col-12 col-md-12 col-lg-6 d-flex flex-column gap-3" @submit.prevent="sendMessage">
                <input type="hidden" name="access_key" value="69f711f6-c7c7-42c6-b9de-552c4693023f">
                <input id="input-name" class="py-3 px-3" type="text" name="name" aria-label="name" placeholder="Your name" required>
                <input id="input-email" class="py-3 px-3" type="email" name="email" aria-label="email" placeholder="Your email" required>
                <input id="input-subject" class="py-3 px-3" type="hidden" name="subject" aria-label="subject" placeholder="Subject" required>
                <textarea id="input-message" class="py-3 px-3" name="message" placeholder="Your message" required></textarea>
                <button id="send-btn" type="submit" class="py-3 mt-5" :disabled="isSubmitting">
                    {{ isSubmitting ? 'Sending...' : 'Send!' }}
                </button>
                <p v-if="submissionMessage" role="status" aria-live="polite">
                    {{ submissionMessage }}
                </p>
            </form>
        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue'

const isSubmitting = ref(false)
const submissionMessage = ref('')

async function sendMessage(event) {
    const form = event.currentTarget
    isSubmitting.value = true
    submissionMessage.value = ''

    try {
        const response = await fetch('https://api.web3forms.com/submit', {
            method: 'POST',
            body: new FormData(form),
        })
        const result = await response.json()

        if (!response.ok || !result.success) {
            throw new Error(result.message || 'Your message could not be sent. Please try again.')
        }

        submissionMessage.value = 'Thanks! Your message has been sent.'
        form.reset()
    } catch (error) {
        submissionMessage.value = error.message || 'Something went wrong. Please try again.'
    } finally {
        isSubmitting.value = false
    }
}
</script>