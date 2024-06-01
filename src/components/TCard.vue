<template>
  <div class="card">
    <div class="header">
      {{ header }}
    </div>
    <div class="content">
      <slot></slot>
    </div>
    <div class="footer" v-if="btnShow || btnBuy">
      <!-- <button v-if="btnShow" @click="$emit('btn-show-clicked')">{{ btnShowLabel }}</button>
      <button v-if="btnBuy" @click="$emit('btn-buy-clicked')">{{ btnBuyLabel }}</button> -->
      <slot name="footer"></slot>
    </div>
  </div>


</template>

<script>

export default {
  name: 'TCard',
  props: {
    header: String,
    content: String,
    btnShow: {
      type: Boolean,
      default: false
    },
    btnBuy: {
      type: Boolean,
      default: false
    },
    btnShowLabel: {
      type: String,
      default: 'show'
    },
    btnBuyLabel: {
      type: String,
      default: 'buy'
    }
  }
}

</script>
<style scoped>
.card {
  width: 200px;
  border: 1px solid #cdcdcd;
  display: flex;
  flex-direction: column;
}
.header {
  font-weight: bold;
  color: #222;
  flex-basis: 50px;
}
.header, .content, .footer {
  padding: .35em .7em;
}
.header {
  border-bottom: 1px solid #cdcdcd;
}
.footer {
  border-top: 1px solid #cdcdcd;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  gap: 1rem;
  flex-basis: 50px;
}
.content {
  flex-grow: 1;
}
</style>