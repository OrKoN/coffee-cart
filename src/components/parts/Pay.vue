<template>
  <button class="pay" type="button" @click="pay()">Total: {{ currency(total) }}</button>
  <PaymentDetails :isShow="isShow" @close="closed()" />
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { mapGetters } from 'vuex';
import { currency } from '../../utils';
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
  border: 4px solid black;
  background: antiquewhite;
  margin: 0 6px;
  font-size: xx-large;
}

button.pay:hover {
  border-color: goldenrod;
  color: goldenrod;
}
</style>
