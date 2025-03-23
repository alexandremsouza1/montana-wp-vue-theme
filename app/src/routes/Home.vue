<template>
    <section>
        <div class="container mx-auto">
            <ImageCarousel />
            <Description />
            <PricingPages />
            <Testimonials />
        </div>
    </section>
</template>
<script>
import PricingPages from '../components/Pricing/PricingPages.vue'
import ImageCarousel from '../components/Carousel/ImageCarousel.vue'
import Description from '../components/Description/index.vue'
import Testimonials from '../components/Testimonials/Testimonials.vue'
export default{
    name: 'Home',
    components: {
        PricingPages,
        ImageCarousel,
        Description,
        Testimonials
    }
}
</script>