<template>
  <transition
    name="custom"
    enter-active-class="animate__animated animate__fadeInDown"
    leave-active-class="animate__animated animate__slideOutRight">
    <div v-if="sliderStatus">
      <div class="align-items-center" :class="sliderState">
        <label for="" class="font-weight-bold mr-2">Max</label>
        <input
          type="text"
          class="form-control mx-2"
          style="width: 60px; text-align: center;"
          v-model="maxAmount"
          @change="$emit('update:maximum', maxAmount)"
        />
        <input
          type="range"
          class="custom-range"
          min="0"
          max="200"
          v-model="maxAmount"
          @input="$emit('update:maximum', maxAmount)"
        />
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: "price-slider",
  data: function () {
    return {
      maxAmount: 50,
    };
  },
  props: ["sliderStatus", "maximum"],
  computed: {
    sliderState: function () {
      return this.sliderStatus ? 'd-flex' : 'd-none';
    }
  }
};
</script>

<style>
.custom-enter,
.custom-leave-to {
  opacity: 0;
}

.custom-enter-active,
.custom-leave-active {
  transition: opacity 1s ease-in-out;
}

.custom-enter-to,
.custom-leave {
  opacity: 1;
}
</style>
