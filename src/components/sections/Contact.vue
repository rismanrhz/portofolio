<script setup>
import { Mail, Phone, Github, Linkedin, Send} from "lucide-vue-next";
import { reactive, ref } from "vue";
import emailjs from "@emailjs/browser";

const loading = ref(false);
const success = ref(false);
const error = ref(false);

const form = reactive({
    name: "",
    email: "",
    message: "",
});

const sendEmail = async () => {
    loading.value = true;
    success.value = false;
    error.value = false;

    try {
        await emailjs.send(
        "service_cr0mzj8",
        "template_vif16xw",
        {
            from_name: form.name,
            from_email: form.email,
            message: form.message,
        },
        "mclxwshrvGIJjE-zB"
        );
        success.value = true;
        form.name = "";
        form.email = "";
        form.message = "";
    } catch (err) {
        console.error(err);
        error.value = true;
    } finally {
        loading.value = false;
    }
};
</script>

<template>
    <section id="contact" class="bg-white dark:bg-slate-950 py-24">
        <div class="mx-auto max-w-7xl px-6">
            <!-- Heading -->
            <div class="mb-16 text-center">
                <p class="text-sm font-semibold uppercase tracking-[0.3em] text-pink-600">Contact</p>
                <h2 class="mt-3 text-4xl font-bold text-slate-900 dark:text-white">Get In Touch</h2>
                <p class="mt-4 text-slate-500 dark:text-slate-400">Let's build something amazing together.</p>
            </div>
            <div class="grid gap-12 lg:grid-cols-2">
                <!-- LEFT -->
                <div data-aos="fade-right">
                    <h3 class="text-3xl font-bold text-slate-900 dark:text-white">Let's Work Together 👋</h3>
                    <p class="mt-5 leading-8 text-slate-600 dark:text-slate-300">
                        I'm always open to discussing new opportunities,
                        collaborations, or freelance projects.
                    </p>
                    <div class="mt-10 space-y-6">
                        <div class="flex items-center gap-4">
                            <Mail class="text-pink-600" />
                            <span class="text-slate-900 dark:text-white">rismanurhaliza30@gmail.com</span>
                        </div>
                        <div class="flex items-center gap-4">
                            <Phone class="text-pink-600" />
                            <span class="text-slate-900 dark:text-white">+62 856-0110-0857</span>
                        </div>
                        <div class="flex items-center gap-4">
                            <Github class="text-pink-600" />
                            <span class="text-slate-900 dark:text-white">github.com/rismanrhz</span>
                        </div>
                        <div class="flex items-center gap-4">
                            <Linkedin class="text-pink-600" />
                            <span class="text-slate-900 dark:text-white">linkedin.com/in/rismanrhz</span>
                        </div>
                    </div>
                </div>
                <!-- RIGHT -->
                <div class="rounded-3xl bg-white dark:bg-slate-800 p-8 shadow-xl" data-aos="fade-left">
                    <form class="space-y-6" @submit.prevent="sendEmail">
                        <input
                            v-model="form.name"
                            type="text"
                            placeholder="Your Name"
                            required
                            class="w-full rounded-xl border border-slate-300 bg-white p-4 text-slate-900 focus:border-pink-500 focus:outline-none dark:border-slate-700 dark:bg-slate-900 dark:text-white"
                        />
                        <input
                            v-model="form.email"
                            type="email"
                            placeholder="Your Email"
                            required
                            class="w-full rounded-xl border border-slate-300 bg-white p-4 text-slate-900 focus:border-pink-500 focus:outline-none dark:border-slate-700 dark:bg-slate-900 dark:text-white"
                        />
                        <textarea
                            v-model="form.message"
                            rows="6"
                            placeholder="Your Message"
                            required
                            class="w-full rounded-xl border border-slate-300 bg-white p-4 text-slate-900 focus:border-pink-500 focus:outline-none dark:border-slate-700 dark:bg-slate-900 dark:text-white"
                        ></textarea>
                        <button
                            type="submit"
                            :disabled="loading"
                            class="flex items-center justify-center gap-3 rounded-xl bg-pink-600 px-8 py-4 font-semibold text-white transition-all duration-300 hover:bg-pink-700 disabled:cursor-not-allowed disabled:opacity-70"
                        >
                            <!-- Loading -->
                            <svg
                                v-if="loading"
                                class="h-5 w-5 animate-spin"
                                xmlns="http://www.w3.org/2000/svg"
                                fill="none"
                                viewBox="0 0 24 24"
                            >
                                <circle
                                    class="opacity-25"
                                    cx="12"
                                    cy="12"
                                    r="10"
                                    stroke="currentColor"
                                    stroke-width="4"
                                />
                                <path
                                    class="opacity-75"
                                    fill="currentColor"
                                    d="M4 12a8 8 0 018-8v4a4 4 0 00-4 4H4z"
                                />
                            </svg>
                            <Send v-else :size="18" />
                            {{ loading ? "Sending..." : "Send Message" }}
                        </button>
                        <p v-if="success" class="rounded-xl bg-green-100 p-4 text-green-700">✅ Message sent successfully!</p>
                        <p v-if="error" class="rounded-xl bg-red-100 p-4 text-red-700">❌ Failed to send message. Please try again.</p>
                    </form>
                </div>
            </div>
        </div>
    </section>
</template>