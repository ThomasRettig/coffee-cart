<template>
  <button data-test="checkout" class="pay" type="button" aria-label="Proceed to checkout" @click="pay()">Total: {{ currency(total) }}</button>
  <PaymentDetails :isShow="isShow" @close="closed()" />
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { mapGetters } from 'vuex';
import { currency, slow } from '../../utils';
import PaymentDetails  from './PaymentDetails.vue';

export default defineComponent({
  name: 'Pay',
  components: { PaymentDetails },
  computed: {
    ...mapGetters({
      total: 'cart/cartTotal'
    })
  },
  data() {
    return {
      isShow: false
    };
  },
  methods: {
    currency,
    pay() {
      slow();
      this.isShow = true;
    },
    closed() {
      this.isShow = false;
    }
  }
})
</script>

<style scoped>
button.pay {
  cursor: pointer;
  border: 2px solid black;
  background: antiquewhite;
  margin: 0 6px;
  font-size: x-large;
  padding: 6px 10px;
}

button.pay:hover {
  border-color: darkorange;
  color: darkorange;
}
</style>
