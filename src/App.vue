<template>
  <TModal :show="showModal" title="ahoj" @close-me="showModal = false" @ok-clicked="onOkClicked">
Lorem ipsum dolor sit amet consectetur adipisicing elit. Nihil, laborum voluptatum ex iusto sequi pariatur enim adipisci quidem provident nemo amet eveniet aliquid, praesentium voluptates porro reprehenderit sed? Incidunt, doloribus.
  </TModal>
  <ul>
    <TransitionGroup name="list">
      <li v-for="(item, index) in items" :key="item + index">{{ item }}</li>
    </TransitionGroup>
  </ul>
  <button @click="addItem">add item</button>
  <div>
    <button @click="showModal = true">show modal</button>
  </div>
</template>

<script>
import TModal from '@/components/TModal.vue'
export default {
  name: 'App',
  data () {
    return {
      items: ['hruška', 'švestka', 'banán'],
      showModal: false
    }
  },
  methods: {
    addItem() {
      this.items.unshift('kiwi')
    },
    onOkClicked() {
      this.showModal = false
    }
  },
  components: { TModal }
}

</script>

<style scoped>
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}

.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}
</style>