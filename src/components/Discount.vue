<template>
  <div class="discount">
    <h4>지금 결제하면 {{ discountNum }}% 할인~</h4>
  </div>
</template>

<script>
export default {
    // Component에 추가될 때 name은 두 단어 이상이 되어야 한다... 이상한 법칙
    name: 'DiscountComponent',
    data() {
        return {

        }
    },
    props : {
        discountNum : Number,
    },
}
</script>

<style>

.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}

</style>