<template>
  <div>
    <div class="row">
      <div
        v-for="cartItem in items"
        :key="cartItem.name"
        class="col-md-4"
        style="border: 1px solid gray"
        :name="cartItem.name"
      />
    </div>
  </div>
</template>

<script>

export default {
  name: 'Cart',
  data: function () {
    return {
      items: []
    }
  },
  created () {
    this.items = this.getCartItems()
  }
}
</script>

<style>

</style>
