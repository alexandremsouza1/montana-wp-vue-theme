<template>
    <section>
        <div class="container mx-auto">
            <ImageCarousel />
            <Description />
            <PricingPages />
        </div>
    </section>
</template>
<script>
import PricingPages from '../components/Pricing/PricingPages.vue'
import ImageCarousel from '../components/Carousel/ImageCarousel.vue'
import Description from '../components/Description/index.vue'
export default{
    name: 'Home',
    components: {
        PricingPages,
        ImageCarousel,
        Description
    }
}
</script>