<script>
import Modal from "../components/Modal.vue";
import HomeBackground from "../components/HomeBackground.vue";

export default {
  components: {
    Modal,
    HomeBackground,
  },
  data() {
    return {
      advice: null,
      isOpen: false,
    };
  },
  methods: {
    getAdvice(url) {
      fetch(url)
        .then((res) => res.json())
        .then((data) => {
          const { slip } = data;
          this.advice = slip?.advice;
        });
    },
    toggleShowModal() {
      this.isOpen = !this.isOpen;
    },
  },
  mounted() {
    this.getAdvice("https://api.adviceslip.com/advice");
  },
};
</script>

<template>
  <main>
    <HomeBackground />
    <button id="button2" @click="toggleShowModal">Click here!!</button>
    <Modal
      :open="isOpen"
      title="Today's Advice"
      :text="advice"
      @close="toggleShowModal"
    />
  </main>
</template>

<style scoped>
main {
  width: 100vw;
  height: 100vh;
  overflow: hidden;

  background-image: url("/public/fundo.jpeg");
  background-repeat: no-repeat;
  background-size: 100%;
  z-index: 1%;
}

#button2 {
  background: transparent;
  border: none;
  color: #490f49;
  animation: pulsate 2s infinite;
  position: relative;
  margin: 17.5% 41.5%;

  font-size: 50px;
  width: 20rem;
  cursor: grab;
}

@keyframes pulsate {
  0% {
    transform: scale(0.9);
  }
  50% {
    transform: scale(1.1);
  }
  100% {
    transform: scale(0.9);
  }
}
</style>
