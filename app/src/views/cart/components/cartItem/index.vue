<template>
  <div class="product">
    <h3 class="code">
      <input type="checkbox" @click="select" checked/>
      <router-link :to="`/products/${product.code}`">
        商品编号: {{product.code}}
      </router-link>
    </h3>
    <div class="actions">
      <button @click="minusCount">-</button>
      <span>数量 {{product.amount}}</span>
      <button @click="plusCount">+</button>
    </div>
  </div>
</template>
<script>
  export default{
    props: {
      product: {
        type: Object,
      },
    },
    methods: {
      // *****传每次修改的boolean值
      select(){
        this.product.boolean=!this.product.boolean
        this.$emit('ischoose',this.product.boolean)
      },
      minusCount(){
        if (this.product.amount >=1) {
            this.$emit('amount-change', this.product.amount - 1)
          }
      },
      plusCount(){
        this.$emit('amount-change', this.product.amount + 1)
      }
    },
  }
</script>

<style scoped src="./styles.css" />
