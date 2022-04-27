<template>
  <transition name="fade">
    <div class="promo">
      <span>It's your lucky day! Get an extra cup of Mocha for $4.</span>
      <div>
        <Cup :item="coffee" :disabled="disabled" />
      </div>
      <div class="buttons">
        <button class="yes" @click="addToCart(coffee.name); close();">Yes, of course!</button>
        <button @click="close()">Nah, I’ll skip</button>
      </div>

    </div>
  </transition>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Cup from "../parts/Cup.vue";
import { mapMutations } from "vuex";

export default defineComponent({
  name: "Promotion",
  components: { Cup },
  emits: ['close'],
  data() {
    return {
      coffee: {
        "name": "(Discounted) Mocha",
        "price": 4,
        "discounted": true,
        "recipe": [
            { "name": "espresso", "quantity": 30 },
            { "name": "chocolate syrup", "quantity": 20 },
            { "name": "steamed milk", "quantity": 25 },
            { "name": "whipped cream", "quantity": 25 }
        ]
    },
      disabled: true
    };
  },
  methods: {
    ...mapMutations("cart", ["addToCart"]),
    close() {
      this.$emit('close');
    }
  },
});
</script>

<style scoped>
.buttons {
  display: flex;
  grid-gap: 10px;
}

.buttons button {
  cursor: pointer;
  min-width: 130px;
  border: 2px solid black;
  padding: 5px;
  transition: 0.2s;
}

.buttons button:hover {
  transform: scale(1.05);
}

.yes {
  background: rgb(198, 218, 181);
}

.promo {
  display: flex;
  justify-items: center;
  align-items: center;
  flex-direction: column;
  grid-gap: 16px;
  font-size: larger;
  border: 4px solid black;
  padding: 10px;
  margin-inline: 20px;
  text-align: center;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
