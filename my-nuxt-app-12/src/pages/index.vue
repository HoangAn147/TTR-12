<script setup lang="ts">
import { onMounted } from 'vue'
import { useHomepageStore } from '@/stores/useItemStore'
import { useSeoMeta } from '#imports'

const homepageStore = useHomepageStore()

onMounted(() => {
  homepageStore.fetchHomepageSections()
})

useSeoMeta({
  title: 'Trang Chủ - My App',
  description: 'Xem phim HD miễn phí, tốc độ cao',
  ogTitle: 'My App Movie',
  ogDescription: 'Kho phim online hấp dẫn',
  ogType: 'website'
})
</script>

<template>
  <div class="content-wrapper">
    <ClientOnly><NavCollapse /></ClientOnly>
    <HeroSection v-if="homepageStore.heroData" :my_hero="homepageStore.heroData" />

    <div class="text-center my-5">
      <NuxtLink to="/movies" class="btn btn-primary mx-2">🎬 Xem Phim</NuxtLink>
      <NuxtLink to="/thiet-ke-website" class="btn btn-outline-primary mx-2">
        💻 Dịch vụ Thiết kế Website
      </NuxtLink>
    </div>

    <ClientsSection v-if="homepageStore.clientsData?.length" :my_client="homepageStore.clientsData" />
    <ServicesSection v-if="homepageStore.servicesData?.length" :my_services="homepageStore.servicesData" />
    <ProcessSection v-if="homepageStore.processData" :my_process="homepageStore.processData" />
    <SolutionsSection v-if="homepageStore.solutionsData?.length" :my_solution="homepageStore.solutionsData" />
    <TeamSection v-if="homepageStore.teamData?.length" :my_team="homepageStore.teamData" />
    <ProjectsSection v-if="homepageStore.projectsData?.length" :my_project="homepageStore.projectsData" />
    <TestimonialsSection v-if="homepageStore.testimonialsData?.length" :my_testimonials="homepageStore.testimonialsData" />
    <FaqSection v-if="homepageStore.faqData?.length" :my_faq="homepageStore.faqData" />
    <FooterSection />


  </div>
</template>
