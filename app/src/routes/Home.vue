<template>
    <section>
        <div class="container mx-auto">
            <PricingPages />
        </div>
    </section>
</template>
<script>
import PricingPages from '../components/Pricing/PricingPages.vue'
export default{
    name: 'Home',
    components: {
        PricingPages
    }
}
</script>