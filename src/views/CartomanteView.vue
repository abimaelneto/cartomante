<script>
import Loader from "../components/Loader.vue";

const CARDS_NUMBER = 3;

export default {
  data() {
    return {
      // Inicializando lista de cards que vc vai utilizar
      cards: [],
      loading: false,
    };
  },
  components: {
    Loader,
  },
  methods: {
    async getCards() {
      try {
        this.loading = true;
        const response = await fetch(
          `https://tarot-api-3hv5.onrender.com/api/v1/cards/random?n=${CARDS_NUMBER}`
        );
        const { cards } = await response.json();
        this.cards = cards;
      } catch (error) {
        console.error(error);
      }

      this.loading = false;
    },
  },
};
</script>
<template>
  <main>
    <div class="about">
      <div id="loading" v-if="loading">
        <loader></loader>
      </div>
      <div class="table-content">
        <div v-for="card in cards" :key="card.name" class="tarot card">
          <h3 class="card-name">{{ card.name }}</h3>
          <div class="card-content">
            <p class="bold">Attributes</p>
            <p>
              {{ card.meaning_rev }}
            </p>
          </div>
          <div class="card-content">
            <p>Description:</p>
            <p>{{ card.meaning_up }}</p>
          </div>
        </div>
      </div>
      <button class="image-button" @click="getCards">Pick your card</button>
    </div>
  </main>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}

.tarot {
  animation: deslizar 1s;
}

#loading {
  position: fixed;
  top: 45%;
}

.table-content {
  display: flex;
  position: fixed;
  top: 13%;
  right: 17.1%;
}

.card {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;

  gap: 2rem;
  width: 380px;
  height: 580px;

  border: 10px solid #dfc897;
  border-radius: 8%;

  text-align: center;

  background-color: whitesmoke;

  padding: 5px;
  margin-left: 2.5rem;
}

.card-name {
  height: 40px;
  width: 90%;
  margin-top: 8px;
  /* margin-bottom: 10px; */
  border: 1px solid white;
  background-color: #dfc897;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 5%;

  font-family: "Bebas Neue", cursive;
  font-size: 20px;
  letter-spacing: 0px;
  word-spacing: 0px;
  color: #2c2b2e;
  font-weight: bold;
  text-decoration: none;
  font-style: italic;
  font-variant: normal;
  text-transform: uppercase;
  text-shadow: 2px 2px 4px white;
}

.card-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  min-height: 150px;
  width: 90%;

  margin-bottom: 8px;
  border: 1px solid white;
  border-radius: 10%;
  padding: 20px;

  background-color: #dfc897;
  color: #2c2b2e;

  font-size: 1.3rem;
  text-align: center;
  font-family: "Dosis", sans-serif;
}

.image-button {
  font-size: 55px;
  font-family: "Merriweather", serif;
  color: #dfc897;
  background: transparent;
  border: none;
  cursor: grab;
  position: fixed;
  bottom: 13%;
}

.about {
  display: flex;
  flex-wrap: wrap;
}

main {
  width: 100vw;
  height: 100vh;
  background-image: url("/public/celestial1.jpeg");
  background-repeat: no-repeat;
  background-size: 100%;
  background-position: center;
  z-index: 1%;
}

@keyframes deslizar {
  0% {
    top: -100px;
    opacity: 0;
  }
  50% {
    opacity: 0.5;
  }
  100% {
    top: 0;
    opacity: 1;
  }
}
</style>
