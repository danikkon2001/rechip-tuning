<template>
  <section class="py-6">
    <div class="container mx-auto px-4 md:px-0">
      <div class="grid gap-6 grid-cols-12">
        <div class="col-span-9">
          <h2 class="text-dark text-4xl font-bold">
            Чип-тюнинг {{ title }}
          </h2>
          <p class="text-lg font-semibold mt-1 text-gray-400">
            Выберите поколение {{ title }}:
          </p>
        </div>
      </div>
      <div v-if="gens.length" class="grid-cols-4 gap-6 grid mt-8">
        <div v-for="(item, index) in gens" :key="index" class="col-span-2 md:col-span-1">
          <nuxt-link :to="`/services/${$route.params.servName}/${$route.params.brandName.toLowerCase()}/${$route.params.model.toLowerCase()}/${item.id}`">
            <div class="h-full bg-white hover:bg-[#DADADA] transition-all rounded-lg p-2.5 text-center select-none">
              <p class="font-bold">{{ item.name }}</p>
              <p>{{ item['year-start'] }} <span v-if="item['year-stop']">- {{ item['year-stop'] }}</span> </p>
            </div>
          </nuxt-link>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import type { Model } from '@/src/types/car'

interface Props{
  gens: Model[]
  title: string
}
// const route = useRoute()
const { gens, title } = defineProps<Props>()

</script>

<style scoped>

</style>
