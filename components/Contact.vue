<script setup lang="ts">
const itemref = ref<HTMLDivElement>();
const loader = ref<boolean>(false);

onMounted(() => {
    const itemObs = new IntersectionObserver(
        (entry) => {
            if (entry[0].isIntersecting) {
                loader.value = true;
                itemObs.unobserve(entry[0].target);
            }
        },
        {
            threshold: 0.5,
        }
    );

    itemObs.observe(itemref.value as Element);
});
</script>
<template>
    <div
        ref="itemref"
        class="w-full sm:w-[40%] flex flex-col items-center justify-center gap-y-4 transition duration-500"
        :class="loader ? 'opacity-1 translate-y-0' : 'opacity-0 translate-y-1/3'"
    >
        <h3 class="text-2xl sm:text-5xl font-semibold capitalize">Get in touch</h3>
        <p class="text-center text-sm sm:text-lg font-light font-serif">
            Currently, I'm open to opportunities and doing collaborations; my inbox is always open. Whether you have a question or just want
            to say hi, I'll try my best to get back to you!
        </p>
        <NuxtLink
            to="mailto:amosk7793@gmail.com"
            target="_blank"
            class="card-tate my-2 sm:my-4 px-6 sm:px-8 py-2 sm:py-3 text-base sm:text-lg font-serif tracking-wide rounded hover:shadow-xl"
        >
            Say Hello
        </NuxtLink>
    </div>
</template>
