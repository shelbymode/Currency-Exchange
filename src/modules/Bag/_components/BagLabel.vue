<script setup lang="ts">
import { getFormatCurrency } from '@/helpers/getFormatCurrency'

const props = defineProps<{
  getActualBagData: {
    oldBagValue: number
    actualBagValue: number
    profitPercent: number
    profitAbsolute: number
  }
}>()
</script>

<template>
  <div class="label">
    <h6 class="label__price">{{ getActualBagData.actualBagValue }} USD</h6>

    <span :class="getFormatCurrency(+getActualBagData.profitAbsolute)">{{ getActualBagData.profitAbsolute }}</span>
    USD
    <span style="border-bottom: 1px $darkGrey solid" :class="getFormatCurrency(+getActualBagData.profitPercent)"
      >({{ getActualBagData.profitPercent }}%)</span
    >
  </div>
</template>

<style lang="scss" scoped>
.label {
  box-shadow: rgba(0, 0, 0, 0.2) 0px 12px 28px 0px, rgba(0, 0, 0, 0.1) 0px 2px 4px 0px, rgba(255, 255, 255, 0.05) 0px 0px 0px 1px inset;
  background-color: $creamy;
  border-radius: 4px;
  @include adaptive-value('font-size', 14, 11);
  margin: 5px auto;
  padding: 10px;
  text-align: center;
  align-self: start;
  width: 90%;

  // label__price

  &__price {
    font-weight: bold;
    padding: 10px 0;
    @include adaptive-value('font-size', 20, 14);
    margin: 0;
    color: #2b2d42;
    text-shadow: 0 0 1px #10002b;
  }
}
</style>
