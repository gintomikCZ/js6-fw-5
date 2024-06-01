<template>
  <div>
    <!-- <TCard header="kuřecí maso" btnBuy btnShow>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Minima doloremque voluptates sit deserunt laboriosam
          porro sapiente quidem! Rem inventore quasi natus iure perferendis nesciunt et facere, repellendus deserunt,
          dignissimos enim.</p>
      <template #footer>
        <button>buy</button>
      </template>
    </TCard>

    <TCard header="jízdní kolo" btnShow btnShowLabel="zajezdi si na něm">
        <ul>
          <li @click="console.log('svestka')">švestka</li>
          <li>jablko</li>
          <li>hruška</li>
        </ul>
      <template #footer>
        <button>buy</button>
      </template>
    </TCard> -->
    <!-- <div v-if="userHasPaid">content</div>
    <div class="square-container">
      <transition name="fade">
        <div class="square" v-if="showSquare">
          <span>26</span>
        </div>
      </transition>
    </div> -->
    <div class="square-container">
      <transition name="from-left">
        <div class="square" v-if="showSquare"></div>
      </transition>
      <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quas magnam tenetur cumque, aut necessitatibus
        inventore quo repudiandae veritatis eius blanditiis laudantium ab officia nihil adipisci minima neque eaque rem
        rerum!</p>
    </div>
    <div>
      <button @click="onClick">{{ showSquare ? 'hide' : 'show' }}</button>
    </div>

    <div class="square-container" style="overflow: visible">
      <transition name="slide-right">
        <div class="square" v-if="showSquare2"></div>
      </transition>
    </div>
    <div>
      <button @click="showSquare2 = !showSquare2">{{ showSquare2 ? 'hide' : 'show' }}</button>
    </div>
  </div>
</template>

<script>
import TCard from '@/components/TCard.vue'
export default {
  name: 'App',
  data () {
    return {
      showSquare: false,
      showSquare2: false
    }
  },
  computed: {
    label () {
      return this.showSquare ? 'hide': 'show'
    }
  },
  methods: {
    onClick () {
      this.showSquare = !this.showSquare
    }
  },
  components: { TCard }
}


</script>

<style scoped>
.container {
  display: flex;
  gap: 1rem;
}
.square {
  width: 100px;
  height: 100px;
  background: lightpink;
  border: 1px solid #afafaf;
  position: relative;
}
.square-container {
  height: 150px;
  width: 400px;
  display: flex;
  justify-content: center;
  overflow: hidden;
  border: 1px solid #cdcdcd;
  margin: auto;

}

.fade-enter-from, .fade-leave-to {
  opacity: 0
}
.fade-enter-to, .fade-leave-from {
  opacity: 1
}
.fade-enter-active, .fade-leave-active {
  transition: opacity 1s ease;
}

.from-left-enter-from, .from-left-leave-to {
  left: -150px;
}
.from-left-enter-to, .from-left-leave-from {
  left: 0;
}
.from-left-enter-active, .from-left-leave-active {
  transition: left 1s linear;
}

.slide-right-enter-from, .slide-right-leave-to {
  transform: scaleX(0);
  opacity: 0;
}
.slide-right-enter-to, .slide-right-leave-from {
  transform: scaleX(1);
  opacity: 1;
}
.slide-right-enter-active, .slide-right-leave-active {
  transition: all 1s linear;
  transform-origin: left;
}


</style>