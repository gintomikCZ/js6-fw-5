<template>
  <transition name="fade" @after-enter="showContent = true">
    <div class="modalbackground" v-if="showInternal">

      <transition name="slide-down" @after-leave="showInternal = false">
        <div class="modal" v-if="showContent">

          <div class="header">
            <div>{{ title }}</div>
            <div @click="showContent = false">X</div>
          </div>

          <div class="body">
            <slot></slot>
          </div>

          <div class="footer">
            <button @click="onOkClick">OK</button>
            <button @click="showContent = false">cancel</button>
          </div>

        </div>
      </transition>

    </div>
  </transition>
</template>

<script>

export default {
  name: 'TModal',
  props: {
    show: Boolean,
    title: String
  },
  data () {
    return {
      showContent: false,
      showInternal: false
    }
  },
  watch: {
    show (newValue) {
      if (!newValue) {
        if (this.showContent) {
          this.showContent = false
        }
      } else {
        this.showInternal = true
      }
    }
  },
  methods: {
    onOkClick () {
      this.$emit('ok-clicked') // do not close modal on this event
    }
  }
}

</script>

<style scoped>
.modalbackground {
  position: fixed;
  background: rgba(0, 0, 0, 0.2);
  left: 0;
  top: 0;
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
.modal {
  background: white;
  width: 300px;
  height: 200px;
  border-radius: 5px;
  display: flex;
  flex-direction: column;

}
.header {
  border-bottom: 1px solid #cdcdcd;
  display: flex;
  justify-content: space-between;
}
.header > div {
  padding: .5rem;
}
.body {
  flex-grow: 1;
  overflow: auto;
}
.body, .footer {
  padding: .5rem;
}
.footer {
  border-top: 1px solid #cdcdcd;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0
}

.fade-enter-to,
.fade-leave-from {
  opacity: 1
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity .5s ease;
}
.slide-down-enter-from, .slide-down-leave-to {
  transform: translateY(-200px);
  opacity: 0;
}
.slide-down-enter-to,
.slide-down-leave-from {
  transform: translateY(0);
  opacity: 1;
}
.slide-down-enter-active,
.slide-down-leave-active {
  transition: all .5s ease;
}

</style>