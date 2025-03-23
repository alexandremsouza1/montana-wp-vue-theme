<template>
    <section id="pricing" class="py-16 bg-white">
      <h2 class="text-center text-2xl font-bold mb-12">Simple, Transparent Pricing</h2>
      
      <div class="grid grid-cols-1 md:grid-cols-3 gap-6 max-w-6xl mx-auto">
        <!-- Starter Plan -->
        <div class="border border-[#e5e7eb] rounded-lg p-8">
          <h3 class="font-bold mb-4">Starter</h3>
          <div class="flex items-end mb-6">
            <span class="text-3xl font-bold">$29</span>
            <span class="text-[#525252] text-sm">/month</span>
          </div>
          
          <ul class="space-y-3 mb-8">
            <li class="flex items-start">
              <span class="text-black mr-2">✓</span>
              <span>Up to 100 licenses</span>
            </li>
            <li class="flex items-start">
              <span class="text-black mr-2">✓</span>
              <span>Basic analytics</span>
            </li>
            <li class="flex items-start">
              <span class="text-black mr-2">✓</span>
              <span>Email support</span>
            </li>
          </ul>
          
          <button @click="createLicense('Starter')" class="w-full py-2 border border-[#e5e7eb] rounded hover:bg-[#fafafa] transition-colors">
            Get Started
          </button>
        </div>
        
        <!-- Professional Plan -->
        <div class="border border-[#e5e7eb] rounded-lg p-8">
          <h3 class="font-bold mb-4">Professional</h3>
          <div class="flex items-end mb-6">
            <span class="text-3xl font-bold">$99</span>
            <span class="text-[#525252] text-sm">/month</span>
          </div>
          
          <ul class="space-y-3 mb-8">
            <li class="flex items-start">
              <span class="text-black mr-2">✓</span>
              <span>Up to 1000 licenses</span>
            </li>
            <li class="flex items-start">
              <span class="text-black mr-2">✓</span>
              <span>Advanced analytics</span>
            </li>
            <li class="flex items-start">
              <span class="text-black mr-2">✓</span>
              <span>Priority support</span>
            </li>
          </ul>
          
          <button @click="createLicense('Professional')" class="w-full py-2 bg-black text-white rounded hover:bg-[#525252] transition-colors">
            Get Started
          </button>
        </div>
        
        <!-- Enterprise Plan -->
        <div class="border border-[#e5e7eb] rounded-lg p-8">
          <h3 class="font-bold mb-4">Enterprise</h3>
          <div class="flex items-end mb-6">
            <span class="text-3xl font-bold">Custom</span>
          </div>
          
          <ul class="space-y-3 mb-8">
            <li class="flex items-start">
              <span class="text-black mr-2">✓</span>
              <span>Unlimited licenses</span>
            </li>
            <li class="flex items-start">
              <span class="text-black mr-2">✓</span>
              <span>Custom features</span>
            </li>
            <li class="flex items-start">
              <span class="text-black mr-2">✓</span>
              <span>24/7 support</span>
            </li>
          </ul>
          
          <button @click="createLicense('Enterprise')" class="w-full py-2 border border-[#e5e7eb] rounded hover:bg-[#fafafa] transition-colors">
            Contact Sales
          </button>
        </div>
      </div>
    </section>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const createLicense = async (plan) => {
    try {
      const response = await fetch('http://localhost:8000/wp-json/lmfwc/v2/licenses', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
          'Authorization': 'Basic ' + btoa('ck_2149196a2756fd73215d869b7f5e6a3d8bb23734:cs_9675777c1ef024308ddf643daf82a02a32f259ad') // Substitua pelas chaves API do WooCommerce
        },
        body: JSON.stringify({
          product_id: plan === 'Starter' ? 12 : plan === 'Professional' ? 14 : 15, // IDs dos produtos no WooCommerce
          license_key: plan, 
          order_id: Math.floor(Math.random() * 100000), // Pode ser substituído pelo ID real da compra
          status: "active",
          user_id: '1' // Capturar email do usuário
        })
        // "product_id": "14",
        // "license_key": "Professional",
        // "expires_at": "2025-12-01",
        // "status": "active",
        // "times_activated_max": 3,
        // "user_id": "1"
      });
  
      const data = await response.json();
      console.log('Licença criada:', data);
      alert(`Licença gerada para o plano ${plan}: ${data.license_key}`);
    } catch (error) {
      console.error('Erro ao gerar licença:', error);
      alert('Erro ao criar a licença.');
    }
  };
  </script>
  
  
  <style scoped>
  /* Any component-specific styles can go here */
  </style>