<script>
export default {
  data() {
    return {
      searchQuery: "",
      adviceList: [],
      advice: "",
      showTextEffect: false,
    };
  },
  methods: {
    searchAdvice() {
      const apiUrl = `https://api.adviceslip.com/advice/search/${this.searchQuery}`;
      fetch(apiUrl)
        .then((response) => response.json())
        .then(({ slips }) => {
          if (!slips || slips.length == 0) {
            this.advice = "Everything is gonna be alright!";
            return;
          }

          this.advice = slips[this.getRandomAdviceIndex(slips.length)].advice;
        })
        .catch((error) => {
          console.error(error);
        });
    },
    getRandomAdviceIndex(number) {
      return Math.floor(Math.random() * number);
    },
  },
  mounted() {
    const mainInput = document.querySelector("input");
    mainInput.focus();
  },
};
</script>

<template>
  <main>
    <h1 class="text-effect" v-if="advice">{{ advice }}</h1>

    <div class="input">
      <input
        v-model="searchQuery"
        placeholder="Give me a word and I will look into your future"
        class="custom-input"
      />
      <button @click="searchAdvice" class="material-icons">visibility</button>
    </div>
  </main>
</template>

<style scoped>
.input {
  width: 28%;
  background-color: #c7bda3;
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  border-radius: 30px;
  position: fixed;
  bottom: 13%;
}

.text-effect {
  padding: 15px;
  font-size: 55px;
  font-weight: bold;
  color: white;
  animation: reveal-text 2s linear forwards;
  font-family: "Bad Script", cursive;
  display: flex;
  text-align: center;
}

.material-icons {
  font-size: 45px;
  -webkit-font-feature-settings: "liga";
  -webkit-font-smoothing: antialiased;
  background: transparent;
  border: none;
  color: white;
  margin-bottom: 10px;

  cursor: grab;
}

@keyframes reveal-text {
  0% {
    width: 0;
    opacity: 0;
    transform: translateX(0%);
  }
  100% {
    width: 100%;
    opacity: 1;
    transform: translateX(0);
  }
}

.custom-input {
  width: 80%;
  height: 50px;
  padding-left: 3px;
  border: none;
  background-color: transparent;
  font-size: 16px;
  color: white;
  font-family: "Merriweather", serif;
  font-size: 20px;
  font-weight: bolder;
}

.custom-input::placeholder {
  color: white;
  font-family: "Merriweather", serif;
  font-weight: bold;
  font-size: 16px;
  letter-spacing: 1px;
  opacity: 0.5;
}

.custom-input:focus {
  outline: none;
}

main {
  width: 100vw;
  height: 100vh;
  background-image: url("/public/celestial1.jpeg");
  background-repeat: no-repeat;
  background-size: 100%;
  background-position: center;
  z-index: 1%;

  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
