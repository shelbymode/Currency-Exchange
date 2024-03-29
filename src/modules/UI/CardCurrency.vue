<script setup lang="ts">
import Badge from '@/modules/UI/Badge.vue'
import CardTitle from '@/modules/UI/CardTitle.vue'
import CardRow from '@/modules/UI/CardRow.vue'
import Card from '@/modules/UI/Card.vue'

import { getFormatCurrency } from '@/helpers/getFormatCurrency'
import { getDegreeCalc } from '@/helpers/getDegreeCalc'
import { openModal } from '@/helpers/openModal'

const props = defineProps<{
  name: string
  changePercent24Hr: number
  priceUsd: number
  marketCapUsd: number
  id: string
  index: number
}>()
</script>

<template>
  <Card class="card">
    <template #header>
      <div class="card__content">
        <CardTitle class="card__title card__title card-title text-center">{{ name }}</CardTitle>
        <Badge class="card__badge">Top {{ index }} currency</Badge>
        <button class="card__button btn-buy btn m-0 px-4 btn-sm btn-outline-success" @click="openModal(id)">Buy</button>
      </div>
    </template>

    <template #main>
      <CardRow title="Price :"> ${{ (+priceUsd).toFixed(2) }} </CardRow>
      <CardRow title="Market capital :"> ${{ getDegreeCalc(marketCapUsd, 9) }} Mrd </CardRow>
      <CardRow title="Change for 24h :">
        <span :class="getFormatCurrency(changePercent24Hr)">{{ (+changePercent24Hr).toFixed(2) }}%</span>
      </CardRow>
    </template>
  </Card>
</template>

<style lang="scss" scoped>
.card {
  box-shadow: rgba(0, 0, 0, 0.19) 0px 10px 20px, rgba(0, 0, 0, 0.23) 0px 6px 6px;
  clip-path: polygon(10% 0, 100% 0, 100% 20%, 100% 90%, 90% 100%, 0 100%, 0% 80%, 0 10%);

  // .card__content

  &__content {
    display: grid;
    grid-template-areas:
      'title button'
      'badge button';
    grid-gap: 1px 10px;

    @media (max-width: $tablet) {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: space-between;
    }
  }

  // .card__title

  &__title {
    grid-area: title;
  }

  // .card__badge

  &__badge {
    grid-area: badge;
  }

  // .card__button

  &__button {
    grid-area: button;
    align-self: center;
  }
}
</style>
