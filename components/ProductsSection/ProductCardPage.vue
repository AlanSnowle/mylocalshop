<template lang="pug">
  .product-card-page.flex.justify-center
    img(:src="'https://www.km20.ru/upload/resize_cache/iblock/089/1800_1800_1/089b2817feabafe8a65690bcd0cf398b.jpg'")
    .product-description
      h1 {{ product.name }}
      p {{ product.description }}
      ProductInfo(:info='product.categories')
      ProductPurchase(@click.native='purchaseProduct' :product='product')
</template>

<script>
import ProductInfo from '~/components/ProductsSection/ProductInfo'
import ProductPurchase from '~/components/ProductsSection/ProductPurchase'

export default {
  name: 'ProductCardPage',
  components: {
    ProductInfo,
    ProductPurchase,
  },
  props: {
    product: {
      type: Object,
      required: true,
    },
  },
  methods: {
    purchaseProduct() {
      this.$router.push(`/checkout?product_id=${this.product.id}`)
    },
  },
}
</script>

<style lang="stylus" scoped>
.product-card-page
  img
    height 700px
  .product-description
    width 100%
    margin-left 64px
    h1
      font-size 40px
      font-weight 700
      text-transform uppercase
    p
      margin-top 40px
      font-weight 300
      font-size 16px
</style>
